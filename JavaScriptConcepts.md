# JavaScript

## DOM
* DOM manipulation is expensive. If your application is big or very dynamic, the time spent in manipulating DOM elements rapidly adds up and you hit a performance bottleneck.
* Angular solved it by **dirty model checking** by updating the DOM only when model changes. It still has problems. The static text eg., p tag is updated every time the model is changed when they have same ancestor which is unneccessary. So, the solution is to add another layer between DOM and the HTML template called **Virtual DOM** proposed by React. 
* Virtual DOM is an in-memory representation of the actual elements that are being created for your page.
```html
<div>
  <div id="header">
    <h1>Hello, {{state.subject}}!</h1>
    <p>How are you today?</p>
  </div>
</div>
```
* The above HTML is represented in DOM as below
```javascript
{
  tag: 'div',
  children: [
    {
      tag: 'div',
      attributes: {
        id: 'header'
      },
      children: [
        {
          tag: 'h1',
          children: 'Hello, World!'
        },
        {
          tag: 'p',
          children: 'How are you today?'
        }
      ]
    }
  ]
}
```
* If the `subject` changes here from `Hello, World!` to `Hello, mom!` then only `h1` tag is surgically updated without updating the whole DOM.
* The repainting of the UI is the most expensive part, and React efficiently ensures that the real DOM receives only batched updates to repaint the UI.
* Frequent DOM manipulations are expensive and performance heavy.
* Virtual DOM is a virtual representation of the real DOM.
* When state changes occur, the virtual DOM is updated and the previous and current version of virtual DOM is compared. This is called “diffing”.
* The virtual DOM then sends a batch update to the real DOM to update the UI.
* React uses virtual DOM to enhance its performance.
* It uses the observable to detect state and prop changes.
* React uses an efficient diff algorithm to compare the versions of virtual DOM.
* It then makes sure that batched updates are sent to the real DOM for repainting or re-rendering of the UI.
* Good way to append multiple DOM elements as children is by using `createDocumentFragment` method as shown below.
```javascript
let a = document.createElement('a');
let container = document.querySelector('.container');
let documentFragment = document.createDocumentFragment();
for (let i = 0; i < 1000; i++) {
    let cloneA = a.cloneNode(true);
    cloneA.text = `Row N° ${i}`;
    documentFragment.appendChild(cloneA);
}
container.appendChild(documentFragment);
```

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
* Use `Number.isNaN` function to check for a number.

## Functions
* Regular functions can be invoked in 4 ways.
  * simple invocation
  * method invocation - object method
  * indirect invocation - call, apply
  * constructor invocation
* pass optional parameters for `null` or `undefined` values. Without considerable amount of refactoring, but for a considerable code readability arguments object should be migrated to rest parameters. 
* The arrow function allows efficiently to bind `this` lexically. It uses the enclosing context and does not define its own `this`.
* Arrow functions don't have `this`, `arguments`. So, it cannot be used for object methods, constructor functions.
