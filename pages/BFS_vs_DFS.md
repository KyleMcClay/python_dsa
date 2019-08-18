---
layout: page
title: Breadth-First Search & Depth-First Search in Python
description: How to use BFS & DFS algorithms in python
---

### Breadth-First Search

<img src="https://kylemcclay.github.io/python_dsa/images/BFS.jpg" alt="Broken" class="inline"/>

- Breadth-First Search
  - Searches a graph by exploring each node closest to the starting point
  - Thinking Visually: imagine tree roots branching out
  - Data Structure = queue

### Depth-First Search

<img src="https://kylemcclay.github.io/python_dsa/images/DFS.jpg" alt="Broken" class="inline"/>

- Depth-First Search
  - Searches a graph by exploring each path one by one.
  - Thinking Visually: imagine spikes coming from a point one by one
  - Data Structure = stack


### Sample problem
[Leetcode Problem 240 Search a 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/)

Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties:

Integers in each row are sorted in ascending from left to right. <br />
Integers in each column are sorted in ascending from top to bottom. <br />
Example:

Consider the following matrix:

[1,   4,  7, 11, 15] <br />
[2,   5,  8, 12, 19] <br />
[3,   6,  9, 16, 22] <br />
[10, 13, 14, 17, 24] <br />
[18, 21, 23, 26, 30] <br />

Given target = 5, return true.

Given target = 20, return false.

### Sample Data

If you want to try this problem out for yourself use the sample data :)

matrix = [ <br />
[1,   4,  7, 11, 15] <br />
[2,   5,  8, 12, 19] <br />
[3,   6,  9, 16, 22] <br />
[10, 13, 14, 17, 24] <br />
[18, 21, 23, 26, 30] <br />
] <br />
target_1 = 5 <br />
target_2 = 20 <br />


### Breadth-First Search Implementation
notes before we get started

The order of search for BFS <br />
step 1 [1] <br />
step 2 [2, 4] <br />
step 3 [3, 5, 7] <br />
step 4 [10, 6, 8, 11] <br />
step 5 [18, 13, 9, 12, 15] <br />
step 6 [21, 14, 16, 19] <br />
step 7 [23, 17, 22] <br />
step 8 [26, 24] <br />
step 9 [30] <br />

any node greater than the target number means the path does not need to be searched anymore

```python
def bfsMatrix(matrix, target):
    # subtracting 1 from are max row/columns because the first row is row zero (0)
    max_rows = len(matrix) - 1
    max_columns = len(matrix[0]) - 1
    queue = [(0,0)]

    while len(queue) != 0:
        # current row, column, node
        m = queue[0][0]
        n = queue[0][1]
        current_node = matrix[m][n]

        # if the current node is less than the target we add to our queue
        if current_node < target:

            # check if the next node will be inside the matrix and if its in the queue
            if (m+1) <= max_rows and (m+1, n) not in queue:
                queue.append((m+1, n))
            if (n+1) <= max_columns and (m, n+1) not in queue:
                queue.append((m, n+1))

        elif current_node > target:
            pass
        elif current_node == target:
            return True

        queue.pop(0)

    return False
```


### Depth-First Search Implementation
The order of search for DFS <br />
step 1 [1, 2, 3, 10, 18, 21] <br />
step 2 [13, 14, 23] <br />
step 3 [17, 26] <br />
step 4 [24] <br />
step 4 [6, 9, 16, 22] <br />
step 5 [5, 8, 12, 19] <br />
step 6 [4, 7, 11, 15] <br />


```python
from collections import deque
def dfsMatrix(matrix, target):
    max_rows = len(matrix) - 1
    max_columns = len(matrix[0]) - 1
    stack = deque()
    stack.append((0,0))
    visited_nodes = set()

    while len(stack) != 0:
        m = stack[0][0]
        n = stack[0][1]
        current_node = matrix[m][n]
        visited_nodes.add((m, n))
        if current_node < target:
            if (n+1) <= max_columns and (m, n+1) not in visited_nodes:
                stack.appendleft((m, n+1))
            if (m+1) <= max_rows and (m+1, n) not in visited_nodes:
                stack.appendleft((m+1, n))
        elif current_node > target:
            pass
        elif current_node == target:
            return True
        stack.remove((m,n))
    return False
```

### Simple Solution Implementation
```python
def searchMatrix(matrix, target):
    return any(target in set(row) for row in matrix)
```
