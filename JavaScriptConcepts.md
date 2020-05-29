# JavaScript

## Variables
* `window` and `document`, for example, are global variables supplied by the browser. In a Node environment, you can access `process` object as a global variable. 

## Loops
* `String, Array, TypedArray, Map`, and `Set` are all built-in iterables, because each of their prototype objects implements an `@@iterator` method.
* The `for...of` statement creates a loop iterating over iterable objects, including: built-in String, Array, array-like objects (e.g., arguments or NodeList), TypedArray, Map, Set, and user-defined iterables.
* The `for...in` statement iterates over the enumerable properties of an object, in an arbitrary order.

## Arrays
* Three dots `...` accepts not only arrays, but any iterable objects (strings, maps, sets, etc).
* To transform arrayLike parameter into an array and return it, use
```javascript
  Array.from(arrayLike, [mapFunction])
  ```
* Surely `.indexOf(element) !== -1` must be replaced with `arr.includes(element, [fromIndex])`. 

## Strings
* ECMAScript 2015 provides a correct method to verify a substring existence: 
```javascript
string.includes(substring, [fromIndex])
```
The method returns a boolean that indicates if substring is a substring of string, optionally starting from an index `fromIndex`. 

## Objects
* `Object.assign()` function from ES2015 is designed to implement this requirement. Native, tested and standardized solution. 

## Functions
* Regular functions can be invoked in 4 ways.
  * simple invocation
  * method invocation - object method
  * indirect invocation - call, apply
  * constructor invocation
* pass optional parameters for `null` or `undefined` values. Without considerable amount of refactoring, but for a considerable code readability arguments object should be migrated to rest parameters. 
* The arrow function allows efficiently to bind `this` lexically. It uses the enclosing context and does not define its own `this`.
* Arrow functions don't have `this`, `arguments`. So, it cannot be used for object methods, constructor functions.
