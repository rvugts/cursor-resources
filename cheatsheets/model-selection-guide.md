# Advanced Model Selection & Agent Strategy Guide

This guide provides a sophisticated framework for selecting the optimal AI model and agentic workflow within Cursor. It is tailored to the **next-generation model suite** (v4/v5/v3 era) currently available in Cursor 2.1.

## 🧠 The Model Landscape: Classes & Capabilities

### 1. The "Reasoning" Class
**Models:** `o3`, `o3 Pro`, `DeepSeek R1`
**Role:** The Architect & Mathematician
These models utilize advanced "chain-of-thought" processing. They pause to think, plan, and verify logic before generating a single line of code.
*   **Best For:**
    *   Solving "impossible" concurrency bugs or race conditions.
    *   Architecting distributed systems or microservices from scratch.
    *   Complex algorithmic optimization (Big O reduction).
*   **Trade-offs:** High latency. Not for "quick fixes." `o3 Pro` is the heavy-hitter for the deepest analysis.
*   **Also Consider:** `DeepSeek V3.1` for a faster, non-reasoning alternative that still excels at systems-level code.

### 2. The "Frontier" Coding Class
**Models:** `Sonnet 4.5`, `Opus 4.5`, `GPT-5.1 Codex Max`, `Gemini 3 Pro`, `Sonnet 4 1M`
**Role:** The Principal Engineer (Daily Driver)
These are your workhorses. They balance massive context windows with state-of-the-art instruction following.
*   **Best For:**
    *   **Composer Mode (Agentic Coding):** `Sonnet 4.5` and `Opus 4.5` are king here due to superior context retention across multiple files.
    *   **Code Generation:** `GPT-5.1 Codex Max` is specifically fine-tuned for programming languages, likely offering the highest syntactical accuracy.
    *   **Large Context & Analysis:** `Gemini 3 Pro` is unmatched for digesting entire documentation sets, legacy codebases, or massive logs in a single prompt.
    *   **Extreme Context (1M tokens):** `Sonnet 4 1M` when you need to ingest an *entire* codebase or multiple large files simultaneously.
    *   **Refactoring:** `Sonnet 4.5` excels at maintaining code style consistency during large refactors.
*   **The Leader:** The **Sonnet** family remains the top recommendation for Cursor's Composer due to its "non-lazy" nature, but `GPT-5.1 Codex` is a strong challenger for pure code generation.
*   **Also Available:** `Sonnet 4`, `Opus 4`, `Gemini 2.5 Pro` — slightly older but still highly capable if you want to conserve premium requests.

### 3. The "Speed & Efficiency" Class
**Models:** `GPT-5.1 Codex Fast`, `Haiku 4.5`, `Gemini 2.5 Flash`, `Grok 4 Fast`, `GPT-5 Mini`, `GPT-5 Nano`
**Role:** The Linter / Junior Dev
Extremely fast, lower cost, perfect for iterative tasks.
*   **Best For:**
    *   Quick syntax corrections.
    *   Terminal commands (`find`, `grep`, `awk` scripts).
    *   Writing simple unit tests or boilerplate.
    *   "Chat" interactions where you need an immediate answer.
*   **Tiered Speed:** `GPT-5 Nano` < `GPT-5 Mini` < `GPT-5.1 Codex Fast` (faster → slower, but also less capable → more capable).

---

## 🤖 Agentic Workflows: Composer vs. Chat

### 0. Cursor's Native Agent: `Composer 1`
Cursor ships with its own purpose-built agentic model called **`Composer 1`**. This is a frontier model specifically trained for Cursor's multi-file editing workflow.
*   **When to Use:** When you want the tightest integration with Cursor's tooling (file creation, terminal commands, etc.).
*   **Trade-off:** Less "general knowledge" than Opus/Sonnet, but potentially faster and more reliable for pure agentic coding tasks within Cursor.

### 1. Cursor Composer (Agent Mode)
*   **The Goal:** Multi-file generation, feature implementation.
*   **Recommended:** `Composer 1`, `Sonnet 4.5`, or `Opus 4.5`.
    *   *Why?* You need a model that "remembers" the plan. `Opus 4.5` has the highest "intelligence density" for complex, multi-step planning, while `Sonnet 4.5` offers a faster, highly capable alternative. `Composer 1` is optimized specifically for Cursor's agent loop.
*   **Strategy:** "Refactor the entire `auth` module to use OAuth2." (Use `Opus 4.5` for the plan, `Sonnet 4.5` or `Composer 1` to execute).

### 2. Cursor Chat
*   **The Goal:** Q&A, single-file debug, explanations.
*   **Recommended:** `GPT-5.1 Codex` or `Gemini 3 Pro`.
    *   *Why?* `GPT-5.1 Codex` is tuned for code specific Q&A. `Gemini 3 Pro` typically has a massive context window, great for pasting in huge logs or documentation.

---

## 🎯 Decision Matrix: Which Model When?

| Scenario | Complexity | Recommended Model | Why? |
| :--- | :--- | :--- | :--- |
| **New Feature (Multi-file)** | High | **Composer 1** / **Sonnet 4.5** / **Opus 4.5** | Context stability is paramount. |
| **Complex Logic / Math** | Extreme | **o3 Pro** / **DeepSeek R1** | Needs "System 2" reasoning capabilities. |
| **Pure Code Gen (Scripting)** | Medium | **GPT-5.1 Codex Max** | Specialized fine-tuning for syntax. |
| **Quick Fixes / Shell** | Low | **Haiku 4.5** / **Grok 4 Fast** / **GPT-5 Nano** | Lowest latency, "good enough" accuracy. |
| **Entire Codebase Analysis** | Extreme | **Sonnet 4 1M** | 1 million token context window. |
| **Documentation Analysis** | High | **Gemini 3 Pro** | Massive context window for reading docs. |
| **Architecture Planning** | High | **o3** (Plan) + **Sonnet 4.5** (Exec) | The "Sandwich" method. |

---

## 💡 Advanced Strategies

### 1. The "Codex" Advantage
You have access to `GPT-5.1 Codex` variants (`Max`, `Fast`, `Mini`).
*   **Always prefer `Codex` models for raw coding tasks** over the generic `GPT-5.1` models. They are likely fine-tuned on valid syntax trees and will hallucinate fewer non-existent libraries.

### 2. The "Sandwich" Method (Next-Gen Edition)
1.  **Plan:** Ask `o3 Pro` or `DeepSeek R1` to design the interface and catch edge cases.
2.  **Build:** Paste that plan into Composer with `Sonnet 4.5` or `Opus 4.5`.
3.  **Polish:** Use `GPT-5.1 Codex Fast` to add comments and fix linting errors.

### 3. Experimental & Emerging Models
*   **Grok Code:** Test this for Python/Rust tasks; typically strong on "unfiltered" coding advice.
*   **DeepSeek V3.1:** Often punches above its weight class for C++/Systems programming.
*   **Kimi K2:** A newer entrant worth testing for general coding tasks — may offer surprising quality.
*   **GPT-5 Pro:** The flagship non-Codex GPT-5; use when you need broad knowledge beyond just code (e.g., explaining business logic).
