# Approaching a problem
[Steps by CTCI](http://www.crackingthecodinginterview.com/uploads/6/5/2/8/6528028/cracking_the_coding_skills_-_v6.pdf)

## Coding signals
[How your interviewer evaluates you](https://yangshun.github.io/tech-interview-handbook/coding-signals)

## Problem Solving Constraints

### Inputs
When a problem is given to you,
* For **String** problems, check for empty strings, white spaces, case sensitiveness, unique values, UTF charset 128 or 256, special characters.
* For **Arrays**, check if array is sorted, has duplicate values, # of times duplicates matter or not, has -ve values empty arrays.
* For **Numbers**, if number can be greater than 2^31, negative numbers allowed or not.
* For **Linked lists**, duplicate nodes exist or not, has atleast two nodes, ask if n is always valid,
* For **Trees**, if BST, can there be nodes with same value. 
* For **BST**, trial with all approaches you can think of if you don't know how to start/given an unknown problem. For example, check with stack, queue, BFS, DFS, pre-order, in-order, post-order, reverse pre-order, range sum queries, upper and lower bounds.
* `In-place` does not mean *"without creating any additional variables!"* Rather, it means *"without creating a new copy of the input."* In general, an in-place function will only create additional variables that are `O(1)` space.
    * **Working in-place is a good way to save time and space.** An in-place algorithm avoids the cost of initializing or copying data structures, and it usually has an O(1) space cost.
    * **But be careful: an in-place algorithm can cause side effects.** Your input is "destroyed" or "altered," which can affect code *outside* of your function. For example:
    * **Generally, out-of-place algorithms are considered safer because they avoid side effects.** You should only use an in-place algorithm if you're space constrained or you're *positive* you don't need the original input anymore, even for debugging.
*	Prefer iteration over recursion to avoid limited stack space by recursion.
* When we see terms such as: "shortest/longest, minimized/maximized, least/most, fewest/greatest, biggest/smallest", We know it's an optimization problem.
* When interviewer gives a sorted list, you can take advantage and use binary tree.
* If there is a brute force solution in time O(N<sup>2</sup>) and space `O(1)`, there must exist 2 solutions 
    * Using a `Map` or `Set` in `O(N)` time and `O(N)` space.
    * Using sorting `O(N log N)` time and `O(1)` space.

### Outputs
* check what should be returned by the algorithm. Is it indexes, arrays, boolean or just length of array?

# Patterns

## Linked List
* Slow and Fast pointer. Use this approach if you can't use extra space. e.g., is list circular / has loop, is list palindrome
* Two pointer - delete nth node from list,
* If the length of linked list is unknown and if we need to traverse to the center of the list, use Slow and fast pointers.
* Adding a dummy node at the head and /or tail might help to handle many edge cases where operations have to be performed at the head or the tail. The presence of dummy nodes ensures that operations will never have be executed on the head or the tail. Dummy nodes remove the headache of writing conditional checks to deal with null pointers. Be sure to remove them at the end of the operation.
* Sometimes linked lists problem can be solved without additional storage. Try to borrow ideas from the for reverse a linked list problem.
* For deletion in linked lists, you can either modify the node values or change the node pointers. You might need to keep a reference to the previous element.
* For partitioning linked lists, create two separate linked lists and join them back together.
* Linked lists problems share similarities with array problems. Think about how you would solve an array problem and apply it to a linked list.
* Try to use more pointers if asked to solve in place. e.g., move odd-even lists.

## Array
* Two pointer technique - It is less buggy because you don't have to consider odd and even length string scenario. e.g., move zeroes, reverse String.
* For merge intervals problems, consider two point technique.
* Try `reversing`, `transposing` 2D matrix as an option e.g., Rotating a 2D matrix
* In 2D matrix problems, there can be situations where you `X`s and `O`s and you need a temp value for the cell like `*`. e.g., [Surrounded Regions](https://leetcode.com/problems/surrounded-regions/)
* sliding window techinque - have `start` and `end` pointers. move `end` pointer till you get desired window and then move `start` pointer to contract the window to check if smaller window solution can be obtained.
* Try to find O(N) solution for sub-array problems. e.g., [max subarray sum](https://leetcode.com/problems/maximum-subarray/)
<details>
	<summary>example with running sum</summary>

```javascript
var maxSubArray = function(nums) {
 let prev = 0;
 let max = -Infinity;

 for (let i = 0; i < nums.length; i++) {
     prev = Math.max(prev + nums[i], nums[i]);
     max = Math.max(max, prev);
 }
 return max;
};
```
</details>

* Try drawing on the board/editor the output we are trying to achieve step by step and this will help you to visualize the solution. e.g., [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/). If you list out the output for each cell, the solution can be visualized as getting the product of all left elements and all right elements of a cell.
* If the cumulative sum(represented by `sum[i]` for sum upto `i`th index) upto two indices is the same, the sum of the elements lying in between those indices is `zero`. Extending the same thought further, if the cumulative sum upto two indices, say i and j is at a difference of k i.e. if `sum[i] − sum[j] = k`, the sum of elements lying between indices i and j is k. We can use this approach when asked for sub-array sums.

## String
* Two pointer technique - palindrome
* If the order of characters within the string matters, `HashMaps` are usually not helpful.
* When a question is about counting the number of palindromes, a common trick is to have two pointers that move outward, away from the middle. Note that palindromes can be even or odd length. For each middle pivot position, you need to check it twice: Once that includes the character and once without the character.
* For substrings, you can terminate early once there is no match. For subsequences, use dynamic programming as there are overlapping subproblems. 
* For most substring problem, we are given a string and need to find a substring of it which satisfy some restrictions. A general way is to use a `hashmap` assisted with `two pointers`.
<details>
   <summary>algorithm to solve substring problems</summary>
   
   ```javascript
   1. Use two pointers: start and end to represent a window.
   2. Move end to find a valid window.
   3. When a valid window is found, move start to find a smaller window.
   ```
</details>

* For substring problems, check if target occurs only once in the source string, are chars in target string unique, what should be returned when there is no answer? [Leetcode discuss](https://leetcode.com/problems/find-all-anagrams-in-a-string/discuss/92007/Sliding-Window-algorithm-template-to-solve-all-the-Leetcode-substring-search-problem.)
* There is a template to solve similar substring problems which can be solved with **sliding window technique**
<details>
<summary>Steps to solve substring problems</summary>

* Add **string length checks** and return `false` or whatever is required
* **Declare** `hashmap`, `start` and `end` pointers, `result` string/array, `counter` variable of target string map size.
* **Initialize a hashmap** of target string. assign its size to counter.
* **Loop through source string** while end pointer is less than source string length;
* **Check for target string chars** in source string and deduct their count in map, decrement counter and increment end pointer.
* If **counter is zero**, perform necessary checks like adding result to array/updating min length of result.
* **Increment start pointer** to contract the window. Add start character to map to find the new window.
* **Return `result`** at the end.
</details>

<details>
	<summary>Minimum window substring problem</summary>

```javascript
 /**
 * @param {string} s
 * @param {string} t
 * @return {string}
 */
var minWindow = function(s, t) {
    if(!s.length || !t.length) return '';
    
    let min = Infinity;
    let res = '';
    let start = 0, end = 0;
    let map = new Map();

    for(let i = 0; i< t.length; i++) {
        let c = t[i];
        map.set(c, map.get(c) + 1 || 1)
    }
    let counter = map.size;

    while(end < s.length) {
        let c = s[end];
        if(map.has(c)) {
            map.set(c, map.get(c) - 1);
            if(map.get(c) == 0) counter--;
        }
        end++;
        while(counter == 0) {
	// doing the below step to add the curr char (if it exists in our target char list) to required list, since we are changing the size of window.
            let c1 = s[start];
            if(map.has(c1)) { 
                map.set(c1, map.get(c1) + 1);
                if(map.get(c1) > 0) counter++;
            }
            if(end - start < min) {
                res = s.substring(start, end);
                min = end - start;
            }
            start++;
        }
    }
    return res;
};
```
</details>


## Stack
* For parenthesis matching problems, consider `stack`. e.g.,
<details>
 <summary>Min remove to make string valid</summary>
 
 ```javascript
 /*
 Input: s = "lee(t(c)o)de)"
 Output: "lee(t(c)o)de"
 */
 var minRemoveToMakeValid = function(s) {
    let stack = [];
    let str = s.split(''); 
    
    for(let i = 0, len = str.length; i < len; i++) {
        if(str[i] === '(') {
            stack.push(i);
        } else if (str[i] === ')') {
            if(stack.length) stack.pop();
            else str[i] = '';
        }
    }
    
    for(const i of stack) {
        str[i] = ''
    }
    
    return str.join('')
};
 ```
</details>

## Trie
* If we need to search among a bunch of strings, `trie` is the best DS.
* Common data structures for looking up strings efficiently are
  * Trie/Prefix Tree
  * Suffix Tree
* Tries are special trees (prefix trees) that make searching and storing strings more efficient. Tries have many practical applications, such as conducting searches and providing autocomplete. It is helpful to know these common applications so that you can easily identify when a problem can be efficiently solved using a trie.
* Sometimes preprocessing a dictionary of words (given in a list) into a trie, will improve the efficiency of searching for a word of length k, among n words. Searching becomes O(k) instead of O(n).

## Heap
* If you see a top or lowest k mentioned in the question, it is usually a sign that a heap can be used to solve the problem.
* If you require the top k elements, use a Min Heap of size k. Iterate through each element, pushing it into the heap. Whenever the heap size exceeds k, remove the minimum element. That will guarantee that you have the k largest elements.
* You can also use `quickselect` algorithm to find kth-any element. Refer the `Search` section above

## Search
* `Quickselect` is a textbook algorithm typically used to solve the problems "find kth something": kth smallest, kth largest, kth most frequent, kth less frequent, etc. It has `O(N)` average time complexity and widely used in practice. It worth to note that its worth case time complexity is O(N<sup>2</sup>), although the probability of this worst-case is negligible. The approach is the same as for quicksort.

> One chooses a pivot and defines its position in a sorted array in a linear time using so-called partition algorithm.

As an output, we have an array where the pivot is on its perfect position in the ascending sorted array, sorted by the frequency. All elements on the left of the pivot are less frequent than the pivot, and all elements on the right are more frequent or have the same frequency.

Hence the array is now split into two parts. If by chance our pivot element took `N - k`th final position, then `k` elements on the right are these top `k` frequent we're looking for. If not, we can choose one more pivot and place it in its perfect position. 
<img src="https://leetcode.com/articles/Figures/347_rewrite/hoare.png" width="650"/> \
If that were a quicksort algorithm, one would have to process both parts of the array. That would result in `O(N log⁡N)` time complexity. In this case, there is no need to deal with both parts since one knows in which part to search for N - kth less frequent element, and that reduces the average time complexity to `O(N)`.
* To find kth-smallest use k and to find kth-largest, use `N - k` where N is # of numbers.
<details>
	<summary>Kth largest element in array code sample with quick select</summary>

```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var findKthLargest = function(nums, k) {
    function getpartition(list, left, right) {
	let pivot = list[right];
	let pivotIndex = left;

	for(let i = left; i <= right; i++) {
	    if(list[i] < pivot) {
		[list[i], list[pivotIndex]] = [list[pivotIndex], list[i]];
		pivotIndex++;
	    }
	}

	[list[pivotIndex], list[right]] = [list[right], list[pivotIndex]];
	return pivotIndex;
    }

    function quickselect(list, left, right, k) {
	let partition = getpartition(list, left, right);

	if(partition === k) return list[k];

	else if(partition < k) {
	    return quickselect(list, partition+1, right, k)
	} else {
	    return quickselect(list, left, partition-1, k)
	}
    }

    return quickselect(nums, 0, nums.length-1, nums.length-k)
};
```
</details>

## Recursion
* Recursion implicitly uses a stack. Hence all recursive approaches can be rewritten iteratively using a stack. Beware of cases where the recursion level goes too deep and causes a stack overflow.
* Recursion will never be `O(1)` space complexity because a stack is involved, unless there is tail call optimization (TCO).

## Backtracking
* If we need to try all combinations(or permutations) of the input, we can either use `recursive backtracking` or `iterative BFS`.
### Steps to solve a backtracking problem (2D board)
* Calculate height and width of the 2D matrix.
* Define a helper function which takes row, column and current parameter e.g., `currIndex`
  * Define boundary conditions `(row < 0 || row >= rowLen || col < 0 || col >= colLen)` for the board. `return false` if you meet these conditions. 
  * Define other false conditions like if the cell value is not what we want. `return false`.
  * `return true` if you meet solution condition e.g, if index is last index. 
  * If the current cell has value we are interested in, mark the cell as visited by `board[x][y] = '*';` 
  * Declare a variable `tempResult` and assign `||` of all the helper function for top, right, bottom, left directions.
  * Reset the cell value to `board[x][y] = word[k];`. 
  * `return tempResult`.
* Call the helper function for each cell in the board and if helper function returns true then `return true`, else `return false`.

## Dynamic Programming
* Recursion in DP can be done with following steps
    -  Evaluate choices
    -  Write recursive function with base cases
    -  Ensure that recursive function has varying parameters each time it is called.
    -  Setup cache and capture intermediate results in it. The size/dimension of cache varies with number of varying parameters passed to recursion. If function takes 2 parameters, cache is of size `cache[size1][size2]`, if 3 then `cache[size1][size2][size3]`.
    -  Return if result is in cache.
    -  Done
* https://leetcode.com/discuss/general-discussion/458695/Dynamic-Programming-Patterns
* A matrix is a 2-dimensional array. Questions involving matrices are usually related to dynamic programming or graph traversal.
* For questions involving traversal or dynamic programming, make a copy of the matrix with the same dimensions that are initialized to empty values. Use these values to store the visited state or dynamic programming table. 
* Many grid-based games can be modeled as a matrix. For example, Tic-Tac-Toe, Sudoku, Crossword, Connect 4, and Battleship. It is not uncommon to be asked to verify the winning condition of the game. For games like Tic-Tac-Toe, Connect 4, and Crosswords, verification has to be done vertically and horizontally. One trick is to write code to verify the matrix for the horizontal cells. Then transpose the matrix, reusing the logic used for horizontal verification to verify originally vertical cells (which are now horizontal).

## Tree
* https://leetcode.com/articles/a-recursive-approach-to-segment-trees-range-sum-queries-lazy-propagation/#
* In-order traversal of a binary tree is insufficient to uniquely serialize a tree. Pre-order or post-order traversal is also required.
* When a question involves a BST, the interviewer is usually looking for a solution which runs faster than `O(n)`.
*  In any `preorder` traversal sequence, the first key corresponds to the root. The subsequence which begins at the second element and ends at the last key less than the root, corresponds to the preorder traversal of the root's left subtree. The final subsequence, consisting of keys greater than the root corresponds to the preorder traversal of the root's right subtree. We recursively reconstruct the BST by recursively reconstructing the left and right subtrees from the two subsequences then adding them to the root.

## Graphs
https://leetcode.com/discuss/general-discussion/655708/graph-for-beginners-problems-pattern-sample-solutions/562734

## DFS
<details>
  <summary>Number of Islands (Click to expand!)</summary>
  
```javascript 
var numIslands = function(grid) {
    let count = 0;
    
    function markIsland(grid, i, j) {
        if(i < 0 || i > grid.length-1 || j < 0 || j > grid[i].length-1) {
            return;
        }
        if(grid[i][j] === '0') return;
        grid[i][j] = '0';
        markIsland(grid, i-1, j)
        markIsland(grid, i+1, j)
        markIsland(grid, i, j-1)
        markIsland(grid, i, j+1)
    }
    
    for(let i = 0; i < grid.length; i++) {
        for(let j = 0; j < grid[i].length; j++) {
            if(grid[i][j] === '1') {
                count++;
                markIsland(grid, i, j)
            }
        }
    }
    
    return count;
};
```
</details>

## BFS
* Try to implement the solution incrementally when generating combinations problems. e.g., phone letter pad combinations, generate parentheses.
