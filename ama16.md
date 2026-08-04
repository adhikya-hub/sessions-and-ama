# AMA

### What is LLM?

**LLM (Large Language Model)** is an AI model trained on massive amounts of text data to understand and generate human-like language.

### Uses
- Answering questions
- Writing content
- Summarizing text
- Translating languages
- Generating code
- Powering AI chatbots

**Examples:** GPT-5.5, Claude, Gemini, Llama.

---

### What is the HTTP QUERY method?

The **HTTP QUERY** method (RFC 10008) is a **safe, idempotent** HTTP method that allows **read-only queries using a request body**.
 
> QUERY is like **GET with a request body** for complex read-only searches.

---

### What is GEO?

**GEO (Generative Engine Optimization)** is the practice of optimizing content so AI-powered search engines and chatbots (such as ChatGPT, Gemini, or Perplexity) can easily understand, cite, and recommend it.

Unlike traditional SEO, GEO focuses on making content useful and structured for AI-generated answers.

---

### `null == undefined` is true or false?

**Answer:** **True**

Example:
```javascript
console.log(null == undefined);   // true
console.log(null === undefined);  // false
```

---

### What is batching in React?

**Batching** is React's optimization technique where multiple state updates are grouped together and result in a **single re-render** instead of multiple re-renders.

Example:
```jsx
setCount(c => c + 1);
setName("John");
setAge(25);
```

React batches these updates and performs **one render**, improving performance.
