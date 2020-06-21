# Big O
* https://www.bigocheatsheet.com/
* <img src="https://miro.medium.com/max/2928/1*5ZLci3SuR0zM_QlZOADv8Q.jpeg" />

1. **Constant**: O(1)

2. **Logarithmic**: O(log n). In computer science, it's usually implied that the base is 2. Log 10 is generally log 10 base 2

3. **Linear**: O(n)

4. **Linearithmic**: O(n log n) quicksort, mergesort

5. **Quadratic**: O(n²)

6. **Cubic**: O(n^3) enumerating all triples of items

7. **Expontential**: O(2^n) enumerating all subsets of n items

8. **Factorial**: O(n!) generating all permutations or orderings of n items

## Time Complexity

* If each node in the tree is visited only once, the time complexity is `O(n)`, where `n` is the number of nodes in the tree. We cannot do better than that, since at the very least we have to visit each node to invert it. Because of recursion, `O(h)` function calls will be placed on the stack in the worst case, where h is the height of the tree. Because `h∈O(n)`, the space complexity is `O(n)`. e.g., inverting a binary tree
* For permutations where position matters (e.g. finding all anagram of a string), backtracking has a time complexity of `O(N!)`.
* Subsets: 2^N, since each element could be absent or present. https://leetcode.com/articles/subsets/#
* Logarithmic time is always base 2. So, when we say `log N`, it actually means log<sub>2</sub>N
* Time complexity to find all subarrays of an array is O(N<sup>2</sup>).

## Space Complexity
* If you need to keep a counter of characters, a common mistake is to say that the space complexity required for the counter is `O(n)`. The space required for a counter is `O(1)` not `O(n)`. This is because the upper bound is the range of characters, which is usually a fixed constant of 26. The input set is just lowercase Latin characters. e.g., Frequency counting of characters will help to determine if two strings are anagrams. This also takes `O(n)` time and `O(1)` space.

# Basic math for coding interviews

## Permutations & Combinations [reference](https://www.mathsisfun.com/combinatorics/combinations-permutations.html)

* When the order doesn't matter, it is a `Combination`. When the order does matter it is a `Permutation`.
* A Permutation is an ordered Combination. To help you to remember, think "Permutation ... Position".
* There are 2 types of permutations.
  * **Repetition is allowed**: e.g., choosing r of something that has n different types, the permutations are: `n × n × ... (r times)` is `n^r`
  * **Repetition not allowed**: where n is the number of things to choose from, and we choose r of them in `n!/(n-r)!`
