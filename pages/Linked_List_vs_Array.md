---
layout: page
title: Linked List vs Array in Python
description: How to use linked list & array data structures in python
---

## Linked List vs Array

<img src="https://kylemcclay.github.io/python_dsa/images\Linked_list_array.jpg" alt="Broken" class="inline"/>

A linked list is a simple data structure which "links" each element to the next element.

An array stores each element in an ordered block of memory.

to give understanding to what this means I will ask a series of questions and explain.

** Find the third element in a linked list & array. **

go to the linked list in memory  
go to the first element  
from the first element find the second element    
from the second element find the third element    


go to the array in memory
go to the third element

** Add a new element for the third element in the linked list & array. **

go to the linked list in memory  
go to the first element  
from the first element find the second element    
from the second element add the new third element and   
connect the old third element to the new third element

go to the array in memory 
add one empty element to the end of the array
copy the second to last element to the last element
copy the third to last element to the second to last element
repeat until at the third element in the array 
add new value for the third element 
