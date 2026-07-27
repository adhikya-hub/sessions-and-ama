# AMA

## 1. Why do React component names start with a capital letter?

React uses capitalization to distinguish between **custom components** and **HTML elements**.

- Lowercase names are treated as built-in HTML tags.
- Uppercase names are treated as React components.

### Example

```jsx
function Header() {
  return <h1>Welcome</h1>;
}

function App() {
  return <Header />;
}
```

If you write:

```jsx
<header />
```

React renders the HTML `<header>` element.

If you write:

```jsx
<Header />
```

React calls the `Header` component.

---

## 2. What are React lifecycle methods?

Lifecycle methods are special methods in **class components** that run at different stages of a component's life.

### Mounting (Component is created)

- `constructor()`
- `render()`
- `componentDidMount()`

Used for:
- API calls
- Event listeners
- Initial setup

### Updating (Props or state change)

- `render()`
- `componentDidUpdate()`

Used for:
- Responding to state or prop changes
- Fetching new data

### Unmounting (Component is removed)

- `componentWillUnmount()`

Used for:
- Cleaning timers
- Removing event listeners
- Canceling subscriptions

### Functional Components

Modern React uses **Hooks** instead of lifecycle methods.

```jsx
useEffect(() => {
  console.log("Mounted");

  return () => {
    console.log("Unmounted");
  };
}, []);
```

---

## 3. What is React?

React is an open-source JavaScript library developed by Meta for building fast and interactive user interfaces.

### Features

- Component-based architecture
- Virtual DOM
- One-way data flow
- JSX
- Reusable components
- Efficient updates

### Example

```jsx
function App() {
  return <h1>Hello React</h1>;
}
```

---

## 4. What is the `temperature` parameter in an LLM?

The **temperature** controls how random or creative the AI's responses are.

### Low Temperature (0–0.3)

- More deterministic
- More consistent
- Best for coding and factual answers

Example:

```
Temperature = 0
2 + 2 = 4
```

### Medium Temperature (0.5–0.8)

- Balanced creativity
- Natural conversations

### High Temperature (1.0+)

- More creative
- More varied responses
- Can produce unexpected answers

Example:

Prompt:
```
Write a story about a dragon.
```

High temperature produces more imaginative and diverse stories.

---

## 5. What is React Router?

React Router is a library used for navigation in React Single Page Applications (SPAs).

It allows users to move between pages without refreshing the browser.

### Features

- Client-side routing
- Dynamic routes
- Nested routes
- Route parameters
- Protected routes

### Example

```jsx
import { BrowserRouter, Routes, Route } from "react-router-dom";

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}
```

---

## 6. Common JavaScript String Methods

| Method | Description |
|---------|-------------|
| `length` | Returns string length |
| `toUpperCase()` | Converts to uppercase |
| `toLowerCase()` | Converts to lowercase |
| `trim()` | Removes whitespace from both ends |
| `includes()` | Checks if text exists |
| `startsWith()` | Checks beginning of string |
| `endsWith()` | Checks ending of string |
| `slice()` | Extracts part of a string |
| `substring()` | Returns part of a string |
| `replace()` | Replaces text |
| `replaceAll()` | Replaces all occurrences |
| `split()` | Converts string into array |
| `charAt()` | Returns character at index |
| `indexOf()` | Returns first index of value |
| `lastIndexOf()` | Returns last index |
| `concat()` | Joins strings |
| `repeat()` | Repeats string |
| `padStart()` | Pads beginning of string |
| `padEnd()` | Pads end of string |

### Example

```javascript
const str = " Hello World ";

console.log(str.trim());
console.log(str.toUpperCase());
console.log(str.includes("World"));
console.log(str.slice(0, 5));
console.log(str.replace("World", "JS"));
```

---

## 7. What is the dependency array in React?

The dependency array is the second argument of `useEffect()`.

It tells React **when the effect should run**.

### Run after every render

```jsx
useEffect(() => {
  console.log("Runs every render");
});
```

### Run only once (on mount)

```jsx
useEffect(() => {
  console.log("Runs once");
}, []);
```

### Run when dependencies change

```jsx
useEffect(() => {
  console.log("User changed");
}, [user]);
```

### Multiple dependencies

```jsx
useEffect(() => {
  console.log("Runs when user or count changes");
}, [user, count]);
```

---

## 8. Why do we need the JavaScript Event Loop?

JavaScript is **single-threaded**, meaning it executes one task at a time.

The Event Loop allows JavaScript to handle asynchronous operations without blocking the main thread.

### How it works

1. Call Stack executes synchronous code.
2. Asynchronous tasks (e.g., `setTimeout`, `fetch`) are handled by the browser or Node.js APIs.
3. Completed callbacks are placed into task queues.
4. The Event Loop moves callbacks to the Call Stack when it is empty.

### Example

```javascript
console.log("Start");

setTimeout(() => {
  console.log("Timer");
}, 0);

console.log("End");
```

### Output

```
Start
End
Timer
```

Even though the timeout is `0`, the callback executes only after the Call Stack becomes empty.

### Why is it needed?

- Enables asynchronous programming.
- Prevents the UI from freezing.
- Allows handling of timers, API requests, and user events efficiently.
- Keeps JavaScript responsive while waiting for slow operations.
