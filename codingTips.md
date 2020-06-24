# Data Structures

## Array

* Use the below to calculate mid-point of an array. It won't overflow if *start* and *end* are large positive numbers. Works even if you are using pointers. It will never overflow as long as ```end >= start```. Don't use ```(start+end)/2``` as it might overflow.
```javascript
start + Math.floor((end-start)/2)
```
* Sorting 2D array eg., merge intervals
```javascript
intervals.sort((a,b) => a[0] != b[0] ? a[0] - b[0] : a[1] - b[1]);
```

* To create an array of size 10 and initialize with -1, use 
```javascript
Array(10).fill(-1)
```
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

* Name variables appropriately and readable. Instead of i and j, for 2 pointer technique, use **start** and **end**. e.g., in binary search use **start**, **mid** and **end**.
* If you have a situation to check current and previous element in a for loop, you can do this still looping for 0 index:
```javascript
for(let i = 0, len = arr.length; i < len; i++) {
  if(i === 0 || arr[i] > arr[i-1]) {
    ...
  }
  ...
}
```
* If you need to loop over array by excluding current element in each iteration use
```javascript
[...arr.slice(0, i), ...arr.slice(i+1)]
```
* To check if value is an array, use 
```javascript
Array.isArray(input)
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
* To convert a char to number, use + prefix or subtract '0' from char.
```javascript
let str = '100';
+str[0]; //outputs 1 instead of '1'

or

str[0] - '0'; //outputs 1 instead of '1'
```

## Linked List

## Hashmap

## Stack
* Use array as Stack. **push** and **pop** methods.

## Queue
* Use array as Queue. **push** for enqueue and **shift** for dequeue.

## Tree
* Tree is an acyclic undirected graph.
* In Binary Search Tree, some times we might need to compare the node's value against lower and upper bounds and not the left and right child values. e.g., valide BST. Here left child's value of node in right sub tree should not only be smaller than parent node but also must be greater than root's value. 
* The number of recursive calls is bound by the height of the tree. In the worst case, the tree is linear and the height is in ```O(n)```. Therefore, space complexity due to recursive calls on the stack is ```O(n)``` in the worst case.
* For DFS, use Stack and for BFS, use Queue.
<details>
  <summary>BST Inorder Iterative</summary>
  
  ```javascript
  function inorderTraversal(root) {
  const stack = [];
  const res = [];

  while (root || stack.length) {
    if (root) {
      stack.push(root);
      root = root.left;
    } else {
      root = stack.pop();
      res.push(root.val);
      root = root.right;
    }
  }
  return res;
}
  ```
</details>

* In BFS, when using queue, if you want the length of each level, declare a second variable that holds the `size` of that level and decrement the variable on each iteration. 
* The function below is used to get height of a tree. This can be helpful while solving many problems. e.g., Smallest Subtree with all the Deepest Nodes
<details>
  <summary>Height of a tree</summary>
  
  ```javascript
  function getHeight(node) {
      if(!node) return 0;
      return 1 + Math.max(getHeight(node.left), getHeight(node.right));
  }
  ```
</details>

## Graph
There are two primary ways of representing graph:
1.  Adjacency list
2.  Adjacency Matrix
* Let us conside the graph below
* <img src="https://adrianmejia.com/images/digraph.png" width="150" />
* The adjacency matrix is one way of representing a graph using a two-dimensional array (`NxN` matrix). In the intersection of nodes, we add `1` (or other weight) if they are connected and `0` or `-` if they are not connected.
```javascript
  a b c d e
a 1 1 - - -
b - - 1 - - 
c - - - 1 -
d - 1 1 - -
```
* Imagine that you need to represent Facebook network as a graph. You would have to create a matrix of `2 billion x 2 billion`, where most of it would be empty! Nobody would know everybody else just a few thousands at most.
* In general, we deal with sparse graphs so the matrix will waste a lot of space. That’s why in most implementation we would use an adjacency list rather than the matrix.
* Graphs can be represented as an adjacency list using an Array (or HashMap) containing the nodes. Each of these node entries includes a list (array, linked list, set, etc.) that list its adjacent nodes.
```javascript
const graph = {
  a: ['a', 'b'],
  b: ['c'],
  c: ['d'],
  d: ['b', 'c']
}
```

### BFS
* BFS visits the nodes **one level at a time**. To prevent visiting the same node more than once, we'll maintain a **visited** object.
* Since we need to process the nodes in a First In First Out fashion, a queue is a good contender for the data structure to use. The time complexity is `O(V+E)`.
<details>
<summary>BFS pseudo code</summary>
  
```javascript
function BFS
   Initialize an empty queue, empty 'result' array & a 'visited' map
   Add the starting vertex to the queue & visited map
   While Queue is not empty:
     - Dequeue and store current vertex
     - Push current vertex to result array
     - Iterate through current vertex's adjacency list:
       - For each adjacent vertex, if vertex is unvisited:
         - Add vertex to visited map
         - Enqueue vertex
   Return result array
```
</details>

<details>
  <summary>BFS code</summary>
  
```javascript
Graph.prototype.bfs = function(start) {
    const queue = [start];
    const result = [];
    const visited = {};
    visited[start] = true;
    let currentVertex;
    while (queue.length) {
      currentVertex = queue.shift();
      result.push(currentVertex);
      this.adjacencyList[currentVertex].forEach(neighbor => {
        if (!visited[neighbor]) {
          visited[neighbor] = true;
          queue.push(neighbor);
        }
      });
    }
    return result;
}
```
</details>

### DFS
* DFS visits the nodes depth wise. Since we need to process the nodes in a Last In First Out manner, we'll use a **stack**.
* Starting from a vertex, we'll push the neighboring vertices to our stack. Whenever a vertex is popped, it is marked visited in our visited object. Its neighboring vertices are pushed to the stack. Since we are always popping a new adjacent vertex, our algorithm will always **explore a new level**. The time complexity is the same as BFS, `O(V+E)`.
<details>
<summary>DFS pseudo code</summary>
  
```javascript
function DFS
   Initialize an empty stack, empty 'result' array & a 'visited' map
   Add the starting vertex to the stack & visited map
   While Stack is not empty:
     - Pop and store current vertex
     - Push current vertex to result array
     - Iterate through current vertex's adjacency list:
       - For each adjacent vertex, if vertex is unvisited:
         - Add vertex to visited map
         - Push vertex to stack
   Return result array
```
</details>
<details>
  <summary>DFS code</summary>
  
```javascript
Graph.prototype.dfsIterative = function(start) {
    const result = [];
    const stack = [start];
    const visited = {};
    visited[start] = true;
    let currentVertex;
    while (stack.length) {
      currentVertex = stack.pop();
      result.push(currentVertex);
      this.adjacencyList[currentVertex].forEach(neighbor => {
        if (!visited[neighbor]) {
          visited[neighbor] = true;
          stack.push(neighbor);
        }
      });
    }
    return result;
}
```
</details>

## Trie

## Search

* Tip to quickly prove the correctness of your binary search algorithm during an interview. We just need to test an input of size 2. Check if it reduces the search space to a single element (which must be the answer). If not, your algorithm will never terminate.
<details>
<summary>code for binary search</summary>
  
```javascript
  function search(list, target) {
      let start = 0;
      let end = list.length-1;

      while(start <= end) {
          let mid = start + Math.floor((end-start)/2);

          if(list[mid] === target) return true;

          if(list[mid] < target) {
              start = mid+1;
          } else {
              end = mid-1;
          }
      }
      return false
  }
```
  
</details>

## Sort
* Merge Sort

## Backtracking
* An algorithmic-technique for solving problems by trying to build a solution incrementally, one piece at a time, removing those solutions that fail to satisfy the constraints of the problem.

## Greedy algorithms
* An algorithmic paradigm that builds up a solution piece by piece, meaning it chooses the next piece that offers the most obvious and immediate benefit but may not be optimal overall solution.

## Divide & Conquer
* **Divide-and-conquer algorithms** partition the problem into disjoint subproblems, solve the subproblems recursively, and then combine their solutions to solve the original problem. In contrast, `dynamic programming` applies when the subproblems overlap - that is, when subproblems share sub subproblems. In this context, a divide-and-conquer algorithm does more work than necessary, repeatedly solving the common subsubproblems.

## Dynamic Programming
* A **dynamic-programming algorithm** solves each subsubproblem just once and then saves its answer in a table, thereby avoiding the work of recomputing the answer every time it solves each subsubproblem.
* We typically apply dynamic programming to ***optimization problems***. Such problems can have many possible solutions. Each solution has a value, and we wish to find a solution with the optimal (minimum or maximum) value.
* We call such a solution *an* optimal solution to the problem, as opposed to *the* optimal solution, since there may be several solutions that achieve the optimal value.
* When developing a dynamic-programming algorithm, we follow a sequence of four steps:
  1. Characterize the structure of an optimal solution.
  2. Recursively define the value of an optimal solution.
  3. Compute the value of an optimal solution, typically in a bottom-up fashion.
  4. Construct an optimal solution from computed information.

![Greedy vs DP vs D&C](https://res.cloudinary.com/practicaldev/image/fetch/s--QOijg1AO--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://skerritt.blog/content/images/2019/06/image-10.png)

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
* Performs better in scenarios involving frequent additions and removals of key-value pairs. `Objects` are not optimized for this scenario.


## Set
