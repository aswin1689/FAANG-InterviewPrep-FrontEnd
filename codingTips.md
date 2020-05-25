# Data Structures

## Array

* If you just want to return the last element of the array without mutating the original array, we can use ```arr.slice(-1)```
* Generating a sequence 
```javascript
const indices = Array.from(Array(10).keys());
console.log(indices); -> (10) [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```
* To generate a random number between 0 and array length, then use 
```javascript
Math.floor(array.length * Math.random())
```
* In a sudoku, if we want index of 3x3 sub grid assuming index of sub grids is 0, 1, 2....7, 8
```javascript
Math.floor(i/3)+(Math.floor(j/3)*3);
```
* To transpose a matrix 
```javascript
for(let i = 0, rowLength = matrix.length; i < rowLength; i++) {
  for(let j = 0; j < i; j++) {
  }
}
```
*	Converting between Set and Array. ```mySet2 = new Set([1, 2, 3, 4])```
* Convert Set object to an Array object. ```let myArr = Array.from(mySet)```
* Intersect can be simulated via ```let intersection = new Set([...set1].filter(x => set2.has(x)))```
* Difference can be simulated via ```let difference = new Set([...set1].filter(x => !set2.has(x)))```
* Use ```start + Math.floor((end-start)/2)``` to calculate mid-point of an array. It won't overflow if *start* and *end* are large positive numbers. Works even if you are using pointers. It will never overflow as long as ```end >= start```. Don't use ```(start+end)/2``` as it might overflow.
* Name variables appropriately and readable. Instead of i and j, for 2 pointer technique, use **start** and **end**. For Binary search use **start**, **mid** and **end**.
* If you have a situation to check current and previous element in a for loop, you can do this still looping for 0 index:
```javascript
for(let i = 0, len = arr.length; i < len; i++) {
  if(i === 0 || arr[i] > arr[i-1]) {
    ...
  }
  ...
}
```

## String

* If string is “abcdef”, shift left of 2 is “cdefab”. Shift right of (str.length-2) = 4 is “cdefab”. So, shift right is same as ```str.length + shift left```.
* Remember that I can use two pointers (e.g., to get the midpoint by having one pointer go twice as fast, or in a sum problem by having the pointers work inward from either end, or to test if a string is a palindrome).
* If you have a lot of strings, try putting them in a prefix tree / trie.
* To clean the input string e.g., in palindrome problem, to remove special chars and spaces, use regex. [regex tutorial](https://medium.com/factory-mind/regex-tutorial-a-simple-cheatsheet-by-examples-649dc1c3f285), [regex tester](https://regex101.com/)
```javascript
const regex = /\W/gm; //replace non alphanumeric character and not underscore with ''
const cleaned = [...str.toLowerCase().replace(regex, '')];
```
or, equivalent of above
```javascript
s = s.replace(/[^A-Za-z0-9]/g, '').toLowerCase();
```
* If we know that the charset is rather small, we can replace the Map with an integer array as direct access table. Commonly used tables are:
```javascript
    int[26] for Letters 'a' - 'z' or 'A' - 'Z'
    int[128] for ASCII
    int[256] for Extended ASCII
```

## Linked List

## Hashmap

## Stack
* Use array as Stack. **push** and **pop** methods.

## Queue
* Use array as Queue. **push** for enqueue and **shift** for dequeue.

## Tree
* In Binary Search Tree, some times we might need to compare the node's value against lower and upper bounds and not the left and right child values. e.g., valide BST. Here left child's value of node in right sub tree should not only be smaller than parent node but also must be greater than root's value. 
* The number of recursive calls is bound by the height of the tree. In the worst case, the tree is linear and the height is in ```O(n)```. Therefore, space complexity due to recursive calls on the stack is ```O(n)``` in the worst case.
* For DFS, use Stack and for BFS, use Queue.
* Iterative means BFS and Recursive means DFS.
* In BFS, when using queue, if you want the length of each level, declare a second variable that holds the size of that level and decrement the variable on each iteration. 
* If the problem involves parsing or tree/graph traversal (or reversal in some way), consider using a stack.

## Graph

## Trie

## Search

* Tip to quickly prove the correctness of your binary search algorithm during an interview. We just need to test an input of size 2. Check if it reduces the search space to a single element (which must be the answer). If not, your algorithm will never terminate.

## Sort
* Merge Sort

## Dynamic Programming

# JavaScript
* The following function returns a random number between min (inclusive) and max (exclusive):
```javascript
function getRandomNumber(min, max) {
  return Math.random() * (max — min) + min;
}
```
* To get a random value between 0 to n, use the function below:
```javascript
function getRandomInt(max) {
  return Math.floor(Math.random() * Math.floor(max));
}

console.log(getRandomInt(30));
// expected output is any number in this range: 0…29
```
* Always use radix for parseInt ```const val = parseInt(inputValue, 10);``` or ```Number(inputValue);```
* ```if ( foo == null ) ...``` checks for both **null** and **undefined**
* If you do not know whether a variable exists (that means, if it was declared) you should check with the typeof operator. For instance
```javascript
if (typeof foo !== 'undefined' ) {
    // foo could get resolved and it's defined
}
```
* To create a circular loop of n elements, when you are at the last element with index i, do ```(i+1)%n```

* To initialize multiple variable in single statement,
```javascript
let a = 1, b = 2;
```
* The **continue** statement terminates execution of the statements in the current iteration of the current or labeled loop, and continues execution of the loop with the next iteration.
* In contrast to the **break** statement, continue does not terminate the execution of the loop entirely: instead,
    * In a ```while``` loop, it jumps back to the condition.
    * In a ```for``` loop, it jumps to the update expression.

## Map
* Map maintains insertion order while iterating. 
* ```console.log(map.values().next()) // outputs { value: 2, done: false }```
* ```map.values().next().value : -1 // this is how to access first value in Map ```
* While looping a Map, the callback has val, key and map in this order.
```javascript
map.forEach((val, key, map) => {...})
```

## Set

# Useful Links
* https://medium.com/dailyjs/cribsheet-for-javascript-coding-interview-f6327a69a6b7
