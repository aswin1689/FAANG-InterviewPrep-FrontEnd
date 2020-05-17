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
* To select the middle element of array for subarrays like if array is of length 12 and you are working on subarray from indexes 7 to 12 in case of quick sort, 
then to find pivot of this subarray, or just to find a middle element in array, you do 
```arr[Math.floor((lowIndex + highIndex) / 2)]```
* Name variables appropriately and readable. Instead of i and j, for 2 pointer technique, use **start** and **end**. For Binary search use **low**, **mid** and **high**.

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

## Linked List

## Hashmap

## Stack

## Queue

## Tree

* If the problem involves parsing or tree/graph traversal (or reversal in some way), consider using a stack.

## Graph

## Trie

# General
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

## Map
* Map maintains insertion order while iterating. 
* ```console.log(map.values().next()) // outputs { value: 2, done: false }```
* ```map.values().next().value : -1 // this is how to access first value in Map ```

## Set

# Useful Links
* https://medium.com/dailyjs/cribsheet-for-javascript-coding-interview-f6327a69a6b7

## Search

* Use binary search to find pivot element.

## Sort
* Merge Sort


## Dynamic Programming


