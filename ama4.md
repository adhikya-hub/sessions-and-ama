# AMA

## What is `await` in JavaScript?

`await` is a keyword used inside an `async` function (or at the top level in ES modules) to pause the execution of that function until a Promise settles (resolves or rejects).

### Without `await`

```js
function getData() {
  return fetch("/api/data");
}

console.log(getData());
```

Output:

```js
Promise { <pending> }
```

### With `await`

```js
async function getData() {
  const response = await fetch("/api/data");
  console.log(response) //can access data here
  return response;
}
```
output is still the same


1. `fetch()` returns a Promise.
2. `await` pauses the function.
3. JavaScript can still do other work.
4. When the Promise resolves, execution continues. (log and return)

`await` does **not block the entire program**. It only pauses the current async function.

---

## What is Lazy Loading?

Lazy loading means loading resources **only when they are needed**, instead of loading everything at the beginning.

```html
<img src="large-image.jpg" loading="lazy">
```

The image loads only when it comes near the viewport.

---

## What is the difference between `throw new Error()` and `throw "some msg"`?

```js
throw new Error("Invalid");
```

Produces an Error object:

```js
{
  message: "Invalid",
  stack: "..."
}
```

Whereas:

```js
throw "Invalid";
```

Throws only a string.

---

## What is Recursion?

Recursion is when a function calls itself.

---

## What is the Event Loop?

The Event Loop is JavaScript's mechanism for handling asynchronous operations while running on a single thread.

### JavaScript Call Stack

JavaScript executes one task at a time.

### Example with `setTimeout`

```js
console.log("Start");

setTimeout(() => {
  console.log("Timer");
}, 0);

console.log("End");
```

Output:

```js
Start
End
Timer
```

1. `console.log("Start")` goes to the Call Stack.
2. `setTimeout()` is handed to the Web APIs.
3. `console.log("End")` executes.
4. Timer finishes.
5. Callback enters the Callback Queue.
6. Event Loop checks whether the Call Stack is empty.
7. Callback moves to the Call Stack and executes.

The Event Loop continuously checks:

> Is the Call Stack empty?

If yes, it pushes waiting callbacks from the queue into the stack.

---

## What is the Return Type of `JSON.stringify()`?

`JSON.stringify()` returns a **string**.

### Example

```js
const user = {
  name: "John",
  age: 25
};

const result = JSON.stringify(user);

console.log(result);
```

Output:

```js
'{"name":"John","age":25}'
```

Used to convert JavaScript objects into JSON strings for:

- API requests
- Local storage
- File transfers

---

## How to Clear an Array?

### Method 1 

```js
arr.length = 0;
```

Example:

```js
let arr = [1, 2, 3];

arr.length = 0;

console.log(arr);
```

Output:

```js
[]
```

### Method 2

```js
arr.splice(0, arr.length);
```

### Method 3

```js
arr = [];
```

---

## What is the Difference Between Synchronous and Asynchronous?

### Synchronous

Tasks execute one after another.

```js
console.log("A");
console.log("B");
console.log("C");
```

Output:

```js
A
B
C
```

Each line waits for the previous one.

### Asynchronous

Tasks can start now and finish later.

```js
console.log("A");

setTimeout(() => {
  console.log("B");
}, 1000);

console.log("C");
```

Output:

```js
A
C
B
```

### Async APIs

- `fetch()`
- `setTimeout()`
- `setInterval()`
- Event listeners

---

## How Can We Change the Style of an Element Using JavaScript?

### Using `.style`

```html
<p id="text">Hello</p>
```

```js
const element = document.getElementById("text");

element.style.color = "red";
element.style.fontSize = "30px";
element.style.backgroundColor = "yellow";
```

---

## What Are the Issues with Callbacks?

Callbacks can cause several problems when heavily nested.

### Callback Hell

```js
getUser(function(user) {
  getOrders(user.id, function(orders) {
    getPayment(orders[0], function(payment) {
      console.log(payment);
    });
  });
});
```

This pyramid shape becomes difficult to read.

### Inversion of Control (IoC)

When using callbacks, you give your function to another function or a library and trust it to execute correctly.

```js
fetchData(() => {
  console.log("Data received");
});
```

Here, `fetchData` controls **when**, **how many times**, and **whether** your callback runs.


### Solution

- Promises
- Async/Await

---

## What is Debouncing?

Debouncing limits how often a function executes.

The function runs only after the user stops triggering an event for a specified time.

### Example: Search Box

Without debouncing:

```js
input.addEventListener("input", search);
```

Typing:

```text
h
he
hel
hell
hello
```

Triggers 5 API calls.

With debouncing:

```js
function debounce(fn, delay) {
  let timer;

  return function () {
    clearTimeout(timer);

    timer = setTimeout(() => {
      fn();
    }, delay);
  };
}
```

Only one API call occurs after typing stops.

---

## Is a Function an Object in JavaScript?

Yes.

Functions are special objects.

### Example

```js
function greet() {
  console.log("Hello");
}
```

Check type:

```js
console.log(typeof greet);
```

Output:

```js
function
```

### Functions Can Have Properties

```js
greet.language = "English";

console.log(greet.language);
```

Output:

```js
English
```

### Functions Are First-Class Citizens

They can be:

- Assigned to variables
- Passed as arguments
- Returned from functions
- Stored in arrays and objects

```js
const fn = greet;
fn();
```

---

## How to Read a JavaScript Stack Trace?

A stack trace shows the chain of function calls that led to an error.

### Example

```js
function a() {
  b();
}

function b() {
  c();
}

function c() {
  throw new Error("Oops!");
}

a();
```

Output:

```text
Error: Oops!
    at c (app.js:9)
    at b (app.js:5)
    at a (app.js:1)
```

### How to Read It

Read from **top to bottom**:

1. `c()` → where the error happened
2. `app.js:9` → file name and line number of the error
3. `b()` → called `c()`
4. `a()` → called `b()`

### Information Stack Trace gives

- Error type (`Error`, `TypeError`, `ReferenceError`, etc.)
- Error message
- Function names
- File names
- Line numbers
- The sequence of function calls that led to the error
