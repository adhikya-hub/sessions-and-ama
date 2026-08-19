# AMA

## Extended Thinking vs Chain of Thought

**Chain of Thought (CoT)** is the model's step-by-step reasoning process used to arrive at an answer.

**Extended Thinking** means giving the model more computation/time to reason through a difficult problem before producing the final answer. It does **not** mean exposing the model's private chain of thought to the user.

---

## Eval vs Testing

**Testing** checks whether an application works correctly for specific cases.

**Eval (evaluation)** measures how well an AI model/application performs against defined criteria or test cases, such as accuracy, relevance, safety, or helpfulness.

---

## What is Chunking?

**Chunking** is the process of splitting a large document into smaller pieces called **chunks**.

It is commonly used in **RAG (Retrieval-Augmented Generation)** so that relevant sections of a document can be retrieved instead of sending the entire document to the model.

**Example:**

```text
Large Document
      ↓
  ┌───────┐
  │Chunk 1│
  ├───────┤
  │Chunk 2│
  ├───────┤
  │Chunk 3│
  ├───────┤
  │  ...  │
  └───────┘
```

## What is the use of `description` in tools?
  
The `description` tells the model **what a tool does and when it should be used**.
  
For example:
  
  ```json
  {
    "name": "get_weather",
    "description": "Gets the current weather for a given city.",
    "input_schema": {
      "type": "object",
      "properties": {
        "city": {
          "type": "string"
        }
      },
      "required": ["city"]
    }
  }
  ```

  ## What is the Event Loop?
  
  The **event loop** is a mechanism that manages asynchronous tasks and allows a program to work on other tasks while waiting for an operation to finish.
  
  For example, when an application is waiting for a network response:
  
  ```text
  Task A → Waiting for network response
                ↓
           Event Loop
                ↓
  Task B → Runs
                ↓
  Task C → Runs
                ↓
  Task A → Response received → Continues
