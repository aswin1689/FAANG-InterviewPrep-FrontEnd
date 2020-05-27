# Approaching a problem
[Steps by CTCI](http://www.crackingthecodinginterview.com/uploads/6/5/2/8/6528028/cracking_the_coding_skills_-_v6.pdf)

## Coding signals
[How your interviewer evaluates you](https://yangshun.github.io/tech-interview-handbook/coding-signals)

## Problem Solving Constraints

### Inputs
When a problem is given to you,
* For String problems, check for empty strings, white spaces, case sensitiveness, unique values, UTF charset 128 or 256, special characters.
* For Arrays, check if array is sorted, has duplicate values, # of times duplicates matter or not, has -ve values empty arrays.
* For Numbers, if number can be greater than 2^31, negative numbers allowed or not.
* For Linked lists, duplicate nodes exist or not, has atleast two nodes, ask if n is always valid,
* For Trees, if BST, can there be nodes with same value. 
* For BST, trial with all approaches you can think of if you don't know how to start/given an unknown problem. For example, check with stack, queue, BFS, DFS, pre-order, in-order, post-order, reverse pre-order, range sum queries, upper and lower bounds.

### Outputs
* check what should be returned by the algorithm. Is it indexes, arrays or just length of arrays?

# Patterns

## Linked List
* Slow and Fast pointer - is list circular / has loop, is list palindrome
* Two pointer - delete nth node from list,
* If the length of linked list is unknown and if we need to traverse to the center of the list, use Slow and fast pointers.
* Adding a dummy node at the head and /or tail might help to handle many edge cases where operations have to be performed at the head or the tail. The presence of dummy nodes ensures that operations will never have be executed on the head or the tail. Dummy nodes remove the headache of writing conditional checks to deal with null pointers. Be sure to remove them at the end of the operation.
* Sometimes linked lists problem can be solved without additional storage. Try to borrow ideas from the for reverse a linked list problem.
* For deletion in linked lists, you can either modify the node values or change the node pointers. You might need to keep a reference to the previous element.
* For partitioning linked lists, create two separate linked lists and join them back together.
* Linked lists problems share similarities with array problems. Think about how you would solve an array problem and apply it to a linked list.
* Try to use more pointers if asked to solve in place. e.g., move odd-even lists.

## Array
* Two pointer technique - move zeroes, reverse String (two pointer is less buggy because you don't have to consider odd and even length string scenario.)
* Try reversing and transposing 2D matrix for rotating or any problem as an option.

## String
* Two pointer technique - palindrome
* If the order of characters within the string matters, so HashMaps are usually not helpful.
* When a question is about counting the number of palindromes, a common trick is to have two pointers that move outward, away from the middle. Note that palindromes can be even or odd length. For each middle pivot position, you need to check it twice: Once that includes the character and once without the character.
* For substrings, you can terminate early once there is no match. For subsequences, use dynamic programming as there are overlapping subproblems. 

## Recursion
* Recursion implicitly uses a stack. Hence all recursive approaches can be rewritten iteratively using a stack. Beware of cases where the recursion level goes too deep and causes a stack overflow.
* Recursion will never be O(1) space complexity because a stack is involved, unless there is tail call optimization (TCO).

## Dynamic Programming
* https://leetcode.com/discuss/general-discussion/458695/Dynamic-Programming-Patterns
* A matrix is a 2-dimensional array. Questions involving matrices are usually related to dynamic programming or graph traversal.
* For questions involving traversal or dynamic programming, make a copy of the matrix with the same dimensions that are initialized to empty values. Use these values to store the visited state or dynamic programming table. 
* Many grid-based games can be modeled as a matrix. For example, Tic-Tac-Toe, Sudoku, Crossword, Connect 4, and Battleship. It is not uncommon to be asked to verify the winning condition of the game. For games like Tic-Tac-Toe, Connect 4, and Crosswords, verification has to be done vertically and horizontally. One trick is to write code to verify the matrix for the horizontal cells. Then transpose the matrix, reusing the logic used for horizontal verification to verify originally vertical cells (which are now horizontal).

## Tree
* https://leetcode.com/articles/a-recursive-approach-to-segment-trees-range-sum-queries-lazy-propagation/#
* In-order traversal of a binary tree is insufficient to uniquely serialize a tree. Pre-order or post-order traversal is also required.
* When a question involves a BST, the interviewer is usually looking for a solution which runs faster than O(n).

## Trie
* Common data structures for looking up strings efficiently are
  * Trie/Prefix Tree
  * Suffix Tree
* Tries are special trees (prefix trees) that make searching and storing strings more efficient. Tries have many practical applications, such as conducting searches and providing autocomplete. It is helpful to know these common applications so that you can easily identify when a problem can be efficiently solved using a trie.
* Sometimes preprocessing a dictionary of words (given in a list) into a trie, will improve the efficiency of searching for a word of length k, among n words. Searching becomes O(k) instead of O(n).

## Heap
* If you see a top or lowest k mentioned in the question, it is usually a sign that a heap can be used to solve the problem.
* If you require the top k elements, use a Min Heap of size k. Iterate through each element, pushing it into the heap. Whenever the heap size exceeds k, remove the minimum element. That will guarantee that you have the k largest elements.
