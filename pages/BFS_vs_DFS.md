---
layout: page
title: Breadth-First Search & Depth-First Search in Python
description: How to use BFS & DFS algorithms in python
---

##Breadth-First Search

<img src="https://kylemcclay.github.io/python_dsa/images/BFS.jpg" alt="Broken" class="inline"/>

- Breadth-First Search
  - searches information by exploring each node closest to the starting point
  - visually: imagine roots branching out
 - Data structure used is a queue

##Depth-First Search

<img src="https://kylemcclay.github.io/python_dsa/images/DFS.jpg" alt="Broken" class="inline"/>

- Depth-First Search
 - searches information by exploring each path one by one.
 - visually: imagine spikes coming one by one
 - Data structure used is a stack


##Sample problem
[Leetcode Problem 240 Search a 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/)

Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties:

Integers in each row are sorted in ascending from left to right.
Integers in each column are sorted in ascending from top to bottom.
Example:

Consider the following matrix:

[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
Given target = 5, return true.

Given target = 20, return false.

# sample data
matrix = [
    [1,   4,  7, 11, 15],
    [2,   5,  8, 12, 19],
    [3,   6,  9, 16, 22],
    [10, 13, 14, 17, 24],
    [18, 21, 23, 26, 30]
]
target_1 = 5
target_2 = 20


##Breadth-First Search Implementaion
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
