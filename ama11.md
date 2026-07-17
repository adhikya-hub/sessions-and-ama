# AMA

## 1. What is scope?

**Scope** determines where variables can be accessed in your code.

JavaScript has three types of scope:

### Global Scope
Variables declared outside any function or block are accessible everywhere.

```javascript
let name = "Alice";

function greet() {
  console.log(name);
}

greet(); // Alice
```

### Function Scope
Variables declared with `var` inside a function can only be accessed within that function.

```javascript
function test() {
  var age = 25;
  console.log(age);
}

test();
// console.log(age); // Error
```

### Block Scope
Variables declared with `let` and `const` are limited to the block (`{}`) in which they are declared.

```javascript
if (true) {
  let x = 10;
  const y = 20;
}

// console.log(x); // Error
// console.log(y); // Error
```

---

## 2. What is lexical scope?

**Lexical scope** means a function can access variables from the scope where it was **defined**, not where it is called.

```javascript
const city = "Hyderabad";

function outer() {
  const name = "Alice";

  function inner() {
    console.log(name);
    console.log(city);
  }

  inner();
}

outer();
```

Output:

```
Alice
Hyderabad
```

Lexical scope is determined at **write time**, not runtime.

---

## 3. What are the different phases in event propagation?

There are three phases:

### 1. Capturing Phase
The event travels from the document down to the target element.

```
document
  ↓
html
  ↓
body
  ↓
div
  ↓
button
```

Use:

```javascript
element.addEventListener("click", handler, true);
```

---

### 2. Target Phase

The event reaches the actual clicked element.

```
button
```

---

### 3. Bubbling Phase

The event travels back up from the target to its ancestors.

```
button
 ↑
div
 ↑
body
 ↑
html
 ↑
document
```

Default `addEventListener()` listens during the bubbling phase.

```javascript
element.addEventListener("click", handler);
```

---

## 4. What is the scope chain?

When JavaScript cannot find a variable in the current scope, it searches the parent scope, then the parent's parent, until the global scope.

This lookup process is called the **scope chain**.

```javascript
const a = 10;

function outer() {
  const b = 20;

  function inner() {
    const c = 30;

    console.log(a);
    console.log(b);
    console.log(c);
  }

  inner();
}

outer();
```

Lookup order:

```
Current Scope
      ↓
Parent Scope
      ↓
Global Scope
```

If the variable is not found anywhere:

```
ReferenceError
```

---

## 5. What are prototypes?

Every JavaScript object has an internal link to another object called its **prototype**.

Objects inherit properties and methods from their prototype.

```javascript
const person = {
  greet() {
    console.log("Hello");
  }
};

const student = Object.create(person);

student.greet();
```

Output:

```
Hello
```

Prototype chain:

```
student
   ↓
person
   ↓
Object.prototype
   ↓
null
```

This is how JavaScript implements inheritance.

---

## 6. What is a function expression?

A function expression is a function assigned to a variable.

```javascript
const greet = function () {
  console.log("Hello");
};

greet();
```

Named function expression:

```javascript
const greet = function sayHello() {
  console.log("Hello");
};
```

Arrow function is also a function expression.

```javascript
const add = (a, b) => a + b;
```

Unlike function declarations, function expressions are **not fully hoisted**.

```javascript
greet(); // Error

const greet = function () {};
```

---

## 7. Difference between Promise.all() and Promise.allSettled()

| Promise.all() | Promise.allSettled() |
|---------------|----------------------|
| Rejects immediately if any promise fails | Waits for all promises |
| Returns only successful values if none fail | Returns status of every promise |
| Used when every promise must succeed | Used when every result matters |

### Promise.all()

```javascript
Promise.all([
  Promise.resolve(1),
  Promise.resolve(2)
]).then(console.log);
```

Output:

```
[1, 2]
```

If one fails:

```javascript
Promise.all([
  Promise.resolve(1),
  Promise.reject("Error")
]);
```

Output:

```
Rejected immediately
```

---

### Promise.allSettled()

```javascript
Promise.allSettled([
  Promise.resolve(1),
  Promise.reject("Error")
]).then(console.log);
```

Output:

```javascript
[
  { status: "fulfilled", value: 1 },
  { status: "rejected", reason: "Error" }
]
```

---

## 8. What is callback hell?

Callback hell occurs when multiple asynchronous operations are nested inside one another, making the code difficult to read and maintain.

Example:

```javascript
login(function () {
  getProfile(function () {
    getOrders(function () {
      makePayment(function () {
        console.log("Done");
      });
    });
  });
});
```

Problems:

- Hard to read
- Difficult to debug
- Difficult to maintain
- Error handling becomes messy

Solution:

- Promises
- async/await

---

## 9. Difference between Promise.race() and Promise.any()

| Promise.race() | Promise.any() |
|----------------|---------------|
| Returns first settled promise | Returns first fulfilled promise |
| May resolve or reject | Ignores rejections until all fail |
| Rejects if first settled rejects | Rejects only if every promise rejects |

### Promise.race()

```javascript
Promise.race([
  Promise.reject("Error"),
  Promise.resolve("Success")
]);
```

Output:

```
Rejected ("Error")
```

---

### Promise.any()

```javascript
Promise.any([
  Promise.reject("Error"),
  Promise.resolve("Success")
]);
```

Output:

```
Success
```

If every promise rejects:

```
AggregateError
```

---

## 10. What is destructuring?

Destructuring extracts values from arrays or properties from objects into variables.

### Array destructuring

```javascript
const arr = [10, 20, 30];

const [a, b] = arr;

console.log(a);
console.log(b);
```

Output:

```
10
20
```

---

### Object destructuring

```javascript
const user = {
  name: "Alice",
  age: 25
};

const { name, age } = user;

console.log(name);
console.log(age);
```

---

Default values:

```javascript
const { city = "Hyderabad" } = {};
```

---

Renaming variables:

```javascript
const { name: username } = user;
```

---

## 11. What are different object methods?

Some commonly used object methods are:

### Object.keys()

Returns all keys.

```javascript
const user = {
  name: "Alice",
  age: 25
};

console.log(Object.keys(user));
```

Output:

```
["name", "age"]
```

---

### Object.values()

Returns all values.

```javascript
console.log(Object.values(user));
```

Output:

```
["Alice", 25]
```

---

### Object.entries()

Returns key-value pairs.

```javascript
console.log(Object.entries(user));
```

Output:

```javascript
[
  ["name", "Alice"],
  ["age", 25]
]
```

---

### Object.assign()

Copies properties.

```javascript
const copy = Object.assign({}, user);
```

---

### Object.freeze()

Makes an object immutable.

```javascript
Object.freeze(user);
```

---

### Object.seal()

Allows updating existing properties but prevents adding or deleting properties.

```javascript
Object.seal(user);
```

---

### Object.hasOwn()

Checks whether a property belongs directly to the object.

```javascript
Object.hasOwn(user, "name");
```

---

## 12. What is event bubbling?

Event bubbling is the process where an event starts at the target element and then propagates upward through its parent elements.

Example:

```html
<div id="parent">
  <button id="child">Click</button>
</div>
```

```javascript
document.getElementById("parent").addEventListener("click", () => {
  console.log("Parent");
});

document.getElementById("child").addEventListener("click", () => {
  console.log("Child");
});
```

Clicking the button prints:

```
Child
Parent
```

The event flows like this:

```
button
   ↑
div
   ↑
body
   ↑
html
   ↑
document
```

To stop bubbling:

```javascript
event.stopPropagation();
```

Event bubbling is commonly used to implement **event delegation**, where a parent handles events for multiple child elements.
