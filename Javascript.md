# Event Loop in JavaScript

This example demonstrates how asynchronous operations are handled by the event loop in JavaScript, showing the order of execution between synchronous (console.log) and asynchronous (setTimeout, Promise) tasks.

<!-- Example -->

console.log('Start');

setTimeout(function() {
console.log('Timeout callback');
}, 0);

Promise.resolve().then(function() {
console.log('Promise resolved');
});

console.log('End');

<!--End Example -->

# Promises in JavaScript

- Promises in JavaScript allow handling asynchronous operations and chaining multiple asynchronous tasks sequentially or in parallel.

<!-- example of chaining Promises. -->

function asyncTask() {
return new Promise((resolve, reject) => {
setTimeout(() => {
resolve('Async task completed');
}, 2000);
});
}

asyncTask()
.then(result => {
console.log(result);
return 'Chained task completed';
})
.then(result => {
console.log(result);
})
.catch(error => {
console.error(error);
});

<!-- End example of chaining Promises. -->

# difference between var, let, and const?

<!-- Example -->

function example() {
var a = 10;
let b = 20;
const c = 30;

console.log(a, b, c);

if (true) {
var a = 50; // Redeclaration and reassignment of 'a'
let b = 60; // Block-scoped variable
const c = 70; // Block-scoped constant

    console.log(a, b, c);

}

console.log(a, b, c);
}

example();

<!-- End Example -->

# Arrow Functions in JavaScript? How do they differ from regular functions.

- This keyword is don't own parent.

<!-- example -->

const numbers = [1, 2, 3, 4, 5];

// Regular function
const squares = numbers.map(function(x) {
return x \* x;
});

// Arrow function
const squaresArrow = numbers.map(x => x \* x);

console.log(squares); // [1, 4, 9, 16, 25]
console.log(squaresArrow); // [1, 4, 9, 16, 25]

<!-- example -->

# Hoisting in JavaScript.

- how variable and function declarations are moved to the top of their scope during the compilation phase in JavaScript.

<!-- Example -->

console.log(myVar); // undefined
var myVar = 10;

// Example with function declaration hoisting
greet(); // "Hello, World!"

function greet() {
console.log('Hello, World!');
}

<!-- Example -->

# concept of Callbacks and how they are used in JavaScript.

- passing functions as arguments to be executed once the operation completes.

<!-- example -->

function fetchData(url, callback) {
fetch(url)
.then(response => response.json())
.then(data => callback(data))
.catch(error => console.error('Error fetching data: ', error));
}

function processData(data) {
console.log('Data received: ', data);
}

fetchData('https://api.example.com/data', processData);

<!-- example -->

# What is this keyword in JavaScript? How does it differ from bind, call, and apply methods?

# difference between == and === operators

- == performs type coercion and compares values
- while === strictly compares both value and type in JavaScript.

console.log(1 == '1'); // true
console.log(1 === '1'); // false

console.log(0 == false); // true
console.log(0 === false); // false

# Promise and Obserable

-> Promise :

- Executes immediately upon creation.
- Cannot be canceled once created.
- Offers limited built-in methods like then(), catch(), and finally().
- Use for single asynchronous operations, like fetching data from an API endpoint once.

-> Obserable

- Lazy execution. It doesn't start producing values until you subscribe to it using the subscribe() method.
- Subscriptions can be canceled using the unsubscribe() method. This stops the observer from receiving further values from the observable.
- Provides a wide range of operators (e.g., map(), filter(), reduce()) to transform and manipulate the data stream.
- Use for scenarios involving multiple values over time, such as:
  Real-time updates from a web socket.
  User input events from a form.
  Handling multiple API calls that depend on each other.

 <!-- Example -->

// Promise
const promise = fetch('https://api.example.com/data')
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error(error));

// Observable
const observable = new Observable(subscriber => {
subscriber.next(1);
subscriber.next(2);
setTimeout(() => subscriber.next(3), 1000);
});

const subscription = observable.subscribe(value => console.log(value));

// Unsubscribe after 2 seconds
setTimeout(() => subscription.unsubscribe(), 2000);

<!-- End Example -->

# differences between promises and async/await

-> Promise :

- Syntax - Promises use chaining methods like .then() and .catch() to handle asynchronous operations.
- Readability - chaining methods in promises can lead to less readable code.
- Error handling - Promises use .catch() to handle errors.
- When to use - Promises are useful when working with existing codebases that rely on them or when compatibility with older JavaScript environments is important

-> Async / Await

- Syntax - Async/await uses the async and await keywords to provide a more synchronous-like syntax.
- Readability - Async/await can make code more readable and maintainable, especially for complex or nested asynchronous operations.
- Error handling - Async/await uses try/catch for error handling.
- When to use - Async/await is built on top of promises to make them more efficient.
