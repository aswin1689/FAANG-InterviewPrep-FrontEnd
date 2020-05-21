# Approaching a problem
[Steps by CTCI](http://www.crackingthecodinginterview.com/uploads/6/5/2/8/6528028/cracking_the_coding_skills_-_v6.pdf)

## Problem Solving Constraints

### Inputs
When a problem is given to you,
* For String problems, check for empty strings, white spaces, case sensitiveness, unique values, UTF charset 128 or 256, special characters.
* For Arrays, check if array is sorted, has duplicate values, # of times duplicates matter or not, has -ve values empty arrays.
* For Numbers, if number can be greater than 2^31, negative numbers allowed or not.
* For Linked lists, duplicate nodes exist or not, has atleast two nodes, ask if n is always valid,
* For Trees, if BST, can there be nodes with same value

### Outputs
* check what should be returned by the algorithm. Is it indexes, arrays or just length of arrays?

# Patterns

## Linked List
* Slow and Fast pointer - is list circular / has loop, is list palindrome
* Two pointer - delete nth node from list,
* If the length of linked list is unknown and if we need to traverse to the center of the list, use Slow and fast pointers.

## Array
* Two pointer technique - move zeroes, 
* Try reversing and transposing 2D matrix for rotating or any problem as an option.

## String
* Two pointer technique - palindrome

## Dynamic Programming
* https://leetcode.com/discuss/general-discussion/458695/Dynamic-Programming-Patterns

## Tree
* Trial with all approaches you can think of if you don't know how to start/given an unknown problem. For example, check with stack, queue, BFS, DFS, pre-order, in-order, post-order, reverse pre-order, range sum queries, upper and lower bounds.
* https://leetcode.com/articles/a-recursive-approach-to-segment-trees-range-sum-queries-lazy-propagation/#
