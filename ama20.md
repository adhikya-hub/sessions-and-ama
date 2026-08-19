# AMA

## 1. What is a Context Window?

A **context window** is the maximum amount of information an AI model can process in a single request.

It can include:

- System instructions
- User messages
- Previous conversation
- Tool results
- Documents or other input
- The model's generated response

The context window is measured in **tokens**, not simply characters or words.

If the conversation becomes too large, older information may need to be removed or summarized to fit within the context window.

---

## 2. What is RAG?

**RAG (Retrieval-Augmented Generation)** is a technique where an AI system retrieves relevant information from an external knowledge source and provides it to the model before generating an answer.

### Typical RAG Pipeline

```text
User Question
      ↓
Retrieve relevant chunks
      ↓
Add chunks to model context
      ↓
LLM generates answer
      ↓
Final Response
```

For example, if you ask a chatbot about information contained in company documents, RAG can search those documents and provide the relevant sections to the model.

---

## 3. What is Adaptive Thinking?

**Adaptive thinking** is the ability to adjust the approach used to solve a problem based on the situation, new information, or feedback.

Instead of following one fixed reasoning strategy, the system can change its approach when needed.

### Example

```text
Problem
   ↓
Try an approach
   ↓
Evaluate the result
   ↓
Is it sufficient?
  ↙       ↘
No        Yes
↓          ↓
Adapt     Answer
approach
↓
Try again
```

For AI systems, adaptive thinking can mean spending more effort on difficult problems and using a simpler approach for straightforward problems.

---

## 4. Types of Chunking in RAG

**Chunking** is the process of splitting documents into smaller pieces before storing and retrieving them in a RAG system.

### 1. Fixed-Size Chunking

Splits text into chunks with a fixed number of tokens or characters.

```text
Document
   ↓
[Chunk 1] [Chunk 2] [Chunk 3] [Chunk 4]
```

**Advantage:** Simple and predictable.

**Disadvantage:** It may split a sentence or idea in the middle.

---

### 2. Semantic Chunking

Splits the document based on **meaning** rather than a fixed size.

Sentences that are semantically related are kept together, while a significant change in topic can create a new chunk.

**Advantage:** Can produce more meaningful chunks for retrieval.

---

### 3. Document-Structure-Based Chunking

Uses the structure of the document, such as:

* Headings
* Sections
* Subsections
* Tables
* Lists

For example:

```text
Document
├── Introduction
├── Installation
├── Configuration
└── Troubleshooting
```

Each logical section can become a chunk or a group of chunks.
