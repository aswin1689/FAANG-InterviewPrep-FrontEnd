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
* Try `reversing`, `transposing` 2D matrix as an option e.g., Rotating a 2D matrix
* sliding window techinque

## String
* Two pointer technique - palindrome
* If the order of characters within the string matters, so HashMaps are usually not helpful.
* When a question is about counting the number of palindromes, a common trick is to have two pointers that move outward, away from the middle. Note that palindromes can be even or odd length. For each middle pivot position, you need to check it twice: Once that includes the character and once without the character.
* For substrings, you can terminate early once there is no match. For subsequences, use dynamic programming as there are overlapping subproblems. 
* sliding window - find all anagrams

## Search
* `Quickselect` is a textbook algorithm typically used to solve the problems "find kth something": kth smallest, kth largest, kth most frequent, kth less frequent, etc. It has `O(N)` average time complexity and widely used in practice. It worth to note that its worth case time complexity is O(N<sup>2</sup>), although the probability of this worst-case is negligible. The approach is the same as for quicksort.

> One chooses a pivot and defines its position in a sorted array in a linear time using so-called partition algorithm.

As an output, we have an array where the pivot is on its perfect position in the ascending sorted array, sorted by the frequency. All elements on the left of the pivot are less frequent than the pivot, and all elements on the right are more frequent or have the same frequency.

Hence the array is now split into two parts. If by chance our pivot element took `N - k`th final position, then `k` elements on the right are these top `k` frequent we're looking for. If not, we can choose one more pivot and place it in its perfect position. 
![quickselect](https://leetcode.com/articles/Figures/347_rewrite/hoare.png)
If that were a quicksort algorithm, one would have to process both parts of the array. That would result in `O(N log⁡N)` time complexity. In this case, there is no need to deal with both parts since one knows in which part to search for N - kth less frequent element, and that reduces the average time complexity to `O(N)`.
* To find kth-smallest use k and to find kth-largest, use `N - k` where N is # of numbers.

## Recursion
* Recursion implicitly uses a stack. Hence all recursive approaches can be rewritten iteratively using a stack. Beware of cases where the recursion level goes too deep and causes a stack overflow.
* Recursion will never be O(1) space complexity because a stack is involved, unless there is tail call optimization (TCO).

## Backtracking
### Steps to solve a backtracking problem (2D board)
* Calculate rowLength, colLength.
* Define a helper function which takes row, column and current parameter e.g., `currIndex`
  * Define boundary conditions `(row < 0 || row >= rowLen || col < 0 || col >= colLen)` for the board. `return false` if you meet these conditions. 
  * Define other false conditions like if the cell value is not what we want. `return false`.
  * `return true` if you meet solution condition e.g, if index is last index. 
  * If the current cell has value we are interested in mark the cell as visited by `board[x][y] = '*';` 
  * Declare a variable `tempResult` and assign || of all the helper function for top, right, bottom, left directions.
  * Reset the cell value to `board[x][y] = word[k];`. 
  * `return tempResult`.
* Call the helper function for each cell in the board and if helper function returns true then `return true`, else `return false`.

## Dynamic Programming
* https://leetcode.com/discuss/general-discussion/458695/Dynamic-Programming-Patterns
* A matrix is a 2-dimensional array. Questions involving matrices are usually related to dynamic programming or graph traversal.
* For questions involving traversal or dynamic programming, make a copy of the matrix with the same dimensions that are initialized to empty values. Use these values to store the visited state or dynamic programming table. 
* Many grid-based games can be modeled as a matrix. For example, Tic-Tac-Toe, Sudoku, Crossword, Connect 4, and Battleship. It is not uncommon to be asked to verify the winning condition of the game. For games like Tic-Tac-Toe, Connect 4, and Crosswords, verification has to be done vertically and horizontally. One trick is to write code to verify the matrix for the horizontal cells. Then transpose the matrix, reusing the logic used for horizontal verification to verify originally vertical cells (which are now horizontal).

## Tree
* https://leetcode.com/articles/a-recursive-approach-to-segment-trees-range-sum-queries-lazy-propagation/#
* In-order traversal of a binary tree is insufficient to uniquely serialize a tree. Pre-order or post-order traversal is also required.
* When a question involves a BST, the interviewer is usually looking for a solution which runs faster than O(n).

## Graphs
https://leetcode.com/discuss/general-discussion/655708/graph-for-beginners-problems-pattern-sample-solutions/562734

## BFS
* Try to implement the solution incrementally when generating combinations problems. e.g., phone letter pad combinations, generate parentheses.

## Trie
* Common data structures for looking up strings efficiently are
  * Trie/Prefix Tree
  * Suffix Tree
* Tries are special trees (prefix trees) that make searching and storing strings more efficient. Tries have many practical applications, such as conducting searches and providing autocomplete. It is helpful to know these common applications so that you can easily identify when a problem can be efficiently solved using a trie.
* Sometimes preprocessing a dictionary of words (given in a list) into a trie, will improve the efficiency of searching for a word of length k, among n words. Searching becomes O(k) instead of O(n).

## Heap
* If you see a top or lowest k mentioned in the question, it is usually a sign that a heap can be used to solve the problem.
* If you require the top k elements, use a Min Heap of size k. Iterate through each element, pushing it into the heap. Whenever the heap size exceeds k, remove the minimum element. That will guarantee that you have the k largest elements.
* You can also use `quickselect` algorithm to find kth-any element. Refer the `Search` section above
