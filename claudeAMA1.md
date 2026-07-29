# Claude AMA

### 1. Difference Between a Chatbot and an AI Agent

**Chatbot:** An AI system that answers user questions through conversation.
**AI Agent:** An AI system that plans, makes decisions, and performs tasks autonomously to achieve a goal.

---

### 2. Strategies for Context Management

| Strategy | What it does |
|----------|---------------|
| **Pruning** | Rewinds the conversation to an earlier message, removing everything that happened after that point. |
| **Compaction** (`/compact` in Claude Code or server-side compaction in the API) | Summarizes the conversation into a shorter version that preserves key information while using fewer tokens. |
| **Clearing** (`/clear` in Claude Code or starting a new API session) | Starts a completely new conversation with an empty context. No previous session information is retained. |
| **Subagent Handoffs** | Creates a subagent with its own isolated context to complete a specific task, then returns only a summary to the main conversation. |

---

### 3. Difference Between Top-K and Top-P

Both control randomness during text generation.

**Top-K:** Model keeps only the **K most likely tokens**.

**Top-P:** Selects the smallest set of tokens whose cumulative probability reaches **P**.

---

### 4. Difference Between `skills.md`, `CLAUDE.md`, and In-Context Instructions

| skills.md | CLAUDE.md | In-Context Instructions |
|------------|-----------|------------------------|
| Defines reusable capabilities/workflows. | Stores project-wide permanent instructions. | Temporary instructions provided in the current prompt. |
| Can be packaged inside plugins. | Lives in the project repository. | Exists only for the current conversation. |
| Reusable across projects. | Loaded automatically for every session. | Not saved after the session. |
| Example: Code review workflow. | Coding standards for a project. | "Reply in bullet points." |

---

### 5. Permission Modes in Claude Code

Permission modes control which actions Claude can perform without asking the user.

| Mode | Description |
|------|-------------|
| **Default** | Reads are allowed. File edits and commands require approval. |
| **Accept Edits** | File edits are auto-approved, but shell commands still require approval. |
| **Plan Mode** | Claude analyzes and creates a plan without making changes. |
| **Auto** | Common safe reads, edits, and commands are automatically approved. Risky actions still require approval. |
| **Don't Ask** | Claude performs nearly all actions without asking. Best for trusted environments. |
| **Bypass Permissions** | Skips permission checks entirely (typically internal/testing use). |

---

# 6. What is a Plugin?

A **plugin** is a versioned package that extends Claude with additional capabilities.

A plugin can include:

- Skills
- Hooks
- Subagents
- MCP servers
- Commands
- Configuration

---

# 7. What is the Description in a Tool?

The **description** tells the LLM:

- What the tool does
- When it should be used
- What inputs it expects
- What outputs it returns

The model reads the description during tool selection.

---

### 8. Lifecycle of an LLM Request

When a user submits a prompt, the LLM begins by processing the request. It combines the **system prompt**, **developer instructions**, **user prompt**, any available **memory**, and **retrieved context** into a single input. This input is then **tokenized**, meaning the text is broken into smaller units called tokens. The system constructs the final context within the model's context window and passes it to the transformer for **model inference**, where attention mechanisms predict the most likely next token. If additional information or actions are required, the model may perform **tool calling** (such as search, calculators, databases, code execution, or MCP servers). After gathering all necessary information, the model **generates the response** token by token. Finally, the output undergoes **post-processing**, including formatting, citations, and safety checks, before the completed response is returned to the user.

---

# 9. What are Hooks?

A Hook allows you to intercept and control tool calls before or after they execute. When you write a specific rule in CLAUDE.md telling the agent to run Prettier after every file edited, the agent will follow it most of the time. Alternatively, a hook makes it happen every single time without exceptions because the hook fires independently of what the model decides to do.

Examples:

PreToolUse
PostToolUse
UserPromptSubmit 
Stop
Notification 
SessionStart
SessionEnd
 
Hooks automatically execute predefined actions when specific events occur.
