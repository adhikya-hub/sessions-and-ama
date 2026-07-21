# AMA

## What is polymorphism?

Polymorphism is an OOP concept where the same method or interface behaves differently depending on the object calling it. In JavaScript, this is commonly achieved through method overriding.

**Example:**
```javascript
class Animal {
  speak() {
    console.log("Animal speaks");
  }
}

class Dog extends Animal {
  speak() {
    console.log("Dog barks");
  }
}

class Cat extends Animal {
  speak() {
    console.log("Cat meows");
  }
}

const animals = [new Dog(), new Cat()];

animals.forEach(animal => animal.speak());
```

**Output:**
```
Dog barks
Cat meows
```

---

## What is the difference between the Microtask Queue and the Macrotask Queue?

| Microtask Queue | Macrotask Queue |
|-----------------|-----------------|
| Higher priority | Lower priority |
| Runs immediately after synchronous code | Runs after all microtasks finish |
| Used by `Promise.then()`, `catch()`, `finally()`, `queueMicrotask()` | Used by `setTimeout()`, `setInterval()`, DOM events |
| Emptied completely before the next macrotask | Executes one task per event loop iteration |

**Example:**
```javascript
console.log("Start");

setTimeout(() => console.log("Timeout"), 0);

Promise.resolve().then(() => console.log("Promise"));

console.log("End");
```

**Output:**
```
Start
End
Promise
Timeout
```

---

## What is the Event Loop?

The Event Loop is the mechanism that coordinates the Call Stack, Web APIs, and task queues. It continuously checks whether the Call Stack is empty. If it is, it first executes all microtasks and then executes one macrotask, repeating this process continuously.

**Execution order:**
1. Run synchronous code.
2. Execute all microtasks.
3. Execute one macrotask.
4. Repeat.

---

## How do you pass data from a child component to a parent component in React?

A child component cannot directly modify a parent's state. Instead, the parent passes a callback function as a prop, and the child calls that function with the data.

**Parent Component**
```jsx
function Parent() {
  const handleData = (data) => {
    console.log(data);
  };

  return <Child sendData={handleData} />;
}
```

**Child Component**
```jsx
function Child({ sendData }) {
  return (
    <button onClick={() => sendData("Hello Parent")}>
      Send Data
    </button>
  );
}
```

---

## Why can't a React component return multiple JSX elements?

A React component must return a single root element because JSX is compiled into a single JavaScript expression (`React.createElement()`).

**Invalid**
```jsx
function App() {
  return (
    <h1>Hello</h1>
    <p>World</p>
  );
}
```

**Using a wrapper element**
```jsx
function App() {
  return (
    <div>
      <h1>Hello</h1>
      <p>World</p>
    </div>
  );
}
```

**Using a Fragment (preferred)**
```jsx
function App() {
  return (
    <>
      <h1>Hello</h1>
      <p>World</p>
    </>
  );
}
```

Fragments group multiple elements without adding an extra DOM node.

---
