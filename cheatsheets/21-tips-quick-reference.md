# 21 Principles for Professional Vibe Coding

This index summarizes the 21 practical tips that underpin the three pillars in the Vibe Coding Playbook. They are **inspired by Sean Kochel's "Supercharge Your Vibe Coding in 21 Easy-to-Apply Tips" YouTube video** and adapted here for a production-grade, enterprise context.

---

## Legend
| Code | Pillar |
|------|--------|
| **(P1)** | **Architect's Mindset** — Plan Before You Prompt |
| **(P2)** | **The Conversation** — Guide, Don't Just Ask |
| **(P3)** | **Disciplined Workflow** — Guardrails and Recovery |

---

## The 21 Tips

### Pillar 1: Architect's Mindset (Plan Before You Prompt)

1.  **Use widely documented tech stacks (P1, P3).** Prefer mainstream, well-documented frameworks, libraries, and cloud services so the AI can rely on accurate documentation instead of guessing APIs.

2.  **Plan extensively before coding (P1).** Spend serious time upfront clarifying requirements, constraints, and architecture with a reasoning model before touching implementation files.

3.  **Start with a detailed spec or PRD (P1).** Write a Product Requirements Document or spec that defines scope, user stories, and acceptance criteria *before* opening Composer.

4.  **Use rules files to enforce standards (P1, P3).** Create `.cursorrules` or project-level rules to encode your team's conventions, linting preferences, and architectural boundaries.

5.  **Leverage MCP servers for external context (P1).** Connect Model Context Protocol servers (databases, documentation, APIs) so the AI has live, accurate data instead of stale training knowledge.

---

### Pillar 2: The Conversation (Guide, Don't Just Ask)

6.  **Be surgical with context (P2, P3).** Share only the minimal set of files and snippets needed for the current step instead of throwing the entire codebase at the AI.

7.  **Ask for multiple solutions and compare (P2).** Regularly request two or three alternative designs or implementations, then choose or hybridize the best one instead of accepting the first answer.

8.  **Control the scope of each prompt (P2, P3).** Phrase prompts around small, concrete tasks that can be fully completed and verified in one iteration.

9.  **Iterate in tight feedback loops (P2).** After each AI response, review, test, and provide immediate feedback before moving to the next task.

10. **Use the right model for the job (P2).** Switch between reasoning models (o3, DeepSeek R1) for planning and frontier models (Sonnet, Codex) for implementation. See the *Model Selection Guide*.

11. **Prompt for explanations, not just code (P2).** Ask the AI to explain *why* it chose an approach; this surfaces hidden assumptions and catches mistakes early.

12. **Refine prompts with meta-prompting (P2).** If a prompt isn't working, ask the AI to improve the prompt itself before re-running.

---

### Pillar 3: Disciplined Workflow (Guardrails and Recovery)

13. **Commit on green and create checkpoints (P3).** Commit every time tests pass and use editor checkpoints to capture stable states before major prompts or refactors.

14. **Use checkpoints and history intelligently (P3).** Treat your git history and tool-specific checkpoints as a safety net you routinely fall back to when an AI-generated change goes bad.

15. **Write tests before implementation (P3).** Follow TDD: define the expected behavior in tests first, then let the AI write code that makes the tests pass.

16. **Run tests continuously (P3).** Keep a terminal open running your test suite in watch mode so failures surface immediately.

17. **Review every diff before accepting (P3).** Never blindly accept AI changes. Read the diff, understand it, and reject or revise anything that looks wrong.

18. **Keep documentation in sync (P3).** Update READMEs, API docs, and inline comments as part of the same commit that changes the code.

19. **Track  status (P3).** Maintain an `IMPLEMENTATION_STATUS.md` or similar file that lists completed, in-progress, and pending tasks.

20. **Automate linting and formatting (P3).** Use pre-commit hooks and CI checks so style issues are caught automatically, freeing you to focus on logic.

21. **Conduct regular retrospectives (P1, P3).** Periodically review what prompts worked, what failed, and refine your rules and templates accordingly.

---

## Quick Reference Table

| # | Tip | Pillar(s) |
|---|-----|-----------|
| 1 | Use widely documented tech stacks | P1, P3 |
| 2 | Plan extensively before coding | P1 |
| 3 | Start with a detailed spec or PRD | P1 |
| 4 | Use rules files to enforce standards | P1, P3 |
| 5 | Leverage MCP servers for external context | P1 |
| 6 | Be surgical with context | P2, P3 |
| 7 | Ask for multiple solutions and compare | P2 |
| 8 | Control the scope of each prompt | P2, P3 |
| 9 | Iterate in tight feedback loops | P2 |
| 10 | Use the right model for the job | P2 |
| 11 | Prompt for explanations, not just code | P2 |
| 12 | Refine prompts with meta-prompting | P2 |
| 13 | Commit on green and create checkpoints | P3 |
| 14 | Use checkpoints and history intelligently | P3 |
| 15 | Write tests before implementation | P3 |
| 16 | Run tests continuously | P3 |
| 17 | Review every diff before accepting | P3 |
| 18 | Keep documentation in sync | P3 |
| 19 | Track implementation status | P3 |
| 20 | Automate linting and formatting | P3 |
| 21 | Conduct regular retrospectives | P1, P3 |
