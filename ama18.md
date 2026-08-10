# AMA

## 1. What is Generative AI?

Generative AI is a type of artificial intelligence that can create new content such as text, images, audio, video, and code based on the data it has learned from.

* ChatGPT — generates text and code
* DALL·E — generates images
* GitHub Copilot — generates code
* Claude — generates text, code, and other content

---

## 2. What is the use of Token Count?

Token count tells us how much text is being processed by an AI model. Tokens are the small pieces into which text is divided.

Token count is useful for:

* **Cost management** — API usage is often charged based on input and output tokens.
* **Context management** — models have a maximum context window, so token count determines how much information can fit.
* **Performance optimization** — fewer unnecessary tokens can reduce latency and cost.
* **Prompt optimization** — helps identify unnecessarily long prompts.
* **Usage tracking** — allows developers to monitor input and output token consumption.

For example, a word may be one token or multiple tokens depending on the word and tokenizer.

---

## 3. What is Babel?

Babel is a JavaScript compiler that converts modern JavaScript code into JavaScript that can be understood by older browsers or environments.

For example, developers can write modern JavaScript such as:

```javascript
const greet = (name) => {
  return `Hello ${name}`;
};
```

Babel can transform it into older JavaScript syntax that has broader browser compatibility.

Babel is commonly used with tools such as React and Webpack.

---

## 4. What are Hooks?


**Hooks** are automated commands or scripts that run when specific events happen in Claude Code.

### Example

```text
Claude edits code
      ↓
Hook triggers
      ↓
Run tests / formatter
      ↓
Claude continues
```

---

## 5. What is the difference between `skills.md` and `CLAUDE.md`?


| `skills.md`                                                         | `CLAUDE.md`                                                          |
| ------------------------------------------------------------------- | -------------------------------------------------------------------- |
| Defines a specific capability or workflow                           | Provides general instructions for Claude                             |
| Usually focused on a particular task                                | Usually applies to a project or directory                            |
| Can contain detailed instructions for performing a specialized task | Can contain coding conventions, project context, commands, and rules |
| Used to teach Claude how to perform a specific skill                | Used to provide persistent project-level guidance                    |

In simple terms:

**`CLAUDE.md` = general instructions and project context**

**`skills.md` = instructions for performing a specific capability or workflow**

The exact behavior can depend on the agent/tooling system being used.

---

## 6. What are the different types of streaming messages and their uses?

When using the Anthropic Messages API with streaming enabled, the response is delivered as a sequence of events instead of waiting for the complete response.

Common streaming events include:

### `message_start`

Marks the beginning of a message.

**Use:** Provides initial message information such as the message ID and initial usage data.

---

### `content_block_start`

Indicates that a new content block has started.

**Use:** Tells the application that a new piece of content, such as text or a tool-use block, is beginning.

---

### `content_block_delta`

Contains incremental updates to a content block.

**Use:** This is the main event used to display generated text progressively.

Example:

```text
Hel
Hello
Hello world
```

Instead of waiting for the entire response, the application can display each piece as it arrives.

---

### `content_block_stop`

Indicates that the current content block has finished.

**Use:** Allows the application to know that a particular content block is complete.

---

### `message_delta`

Contains updates to the overall message, such as final usage information or stop information.

**Use:** Useful for tracking final token usage and understanding why generation stopped.

---

### `message_stop`

Indicates that the entire streamed message has finished.

**Use:** Signals that the complete response has been received and processing can finish.

### Streaming Flow

```text
message_start
      ↓
content_block_start
      ↓
content_block_delta
      ↓
content_block_delta
      ↓
content_block_stop
      ↓
message_delta
      ↓
message_stop
```

The main benefit of streaming is that users can **see the response being generated progressively**, rather than waiting for the complete response before anything is displayed.
