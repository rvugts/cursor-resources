# Cursor Agent Skills

Custom agent skills invoked with `/skill-name` or applied automatically when the agent detects a matching task. Skills are instruction files (`SKILL.md`) that give the agent domain-specific knowledge and step-by-step workflows.

> **Note:** Agent Skills were introduced in [Cursor 2.4](https://cursor.com/changelog/2-4) (January 2026) and are a recent addition. Compared to always-on rules, skills are better for dynamic context and procedural “how-to” instructions.

## Installation

### Global Skills (Recommended)

Available in all projects:

```bash
mkdir -p ~/.cursor/skills
cp -r refactor-python audit-security create-prompt run-prompt create-spec create-tasks ~/.cursor/skills/
```

### Project-Specific Skills

For team sharing via version control:

```bash
mkdir -p .cursor/skills
cp -r refactor-python audit-security create-prompt run-prompt create-spec create-tasks .cursor/skills/
```

Each skill must stay in its own folder containing a `SKILL.md` file. Cursor discovers skills at startup; no extra registration is needed.

## Available Skills

### Code Quality

- **`refactor-python`** – Refactor Python code (DRY, 25-line functions, type hints, no behavior change).
- **`audit-security`** – Security audit against OWASP Top 10; writes `SECURITY_AUDIT_REPORT.md`.

### Specification-Driven Development (SDD)

- **`create-spec`** – Produce a production-grade specification at `docs/specs/spec.md` via a guided intake → analysis → decision-gate → generation flow. Scales from simple to complex projects, with stack-specific guidance and automatic archival of replaced specs.
- **`create-tasks`** – Decompose the active spec at `docs/specs/spec.md` into atomic, TDD-ready tasks in `docs/specs/tasks.md`. Enforces dependency ordering, testability, and AI-executable granularity; archives prior task lists automatically.

### Meta-Prompting (Advanced)

- **`create-prompt`** – Interview mode to build prompts; saves numbered files under `./prompts/`.
- **`run-prompt`** – Run one or more prompts from `./prompts/` (single, or sequential batch).

## Usage

**Manual invocation:** In Composer or any agent conversation, type `/` and pick a skill (e.g. `/refactor-python`).

**Automatic:** The agent can apply a skill when it decides the task matches the skill’s description (e.g. “refactor this Python file” may trigger `refactor-python`).

Example with context:

```
/refactor-python @my_module.py
```

```
/audit-security @api/auth.py Check for SQL injection and XSS
```

```
/create-spec Build a user authentication service with email + OAuth
```

```
/create-tasks
```

(run `/create-tasks` with no args once `docs/specs/spec.md` exists; it will locate the active spec automatically)

## References

- [Cursor docs: Skills](https://cursor.com/docs/context/skills)
- [Cursor 2.4 Changelog – Skills](https://cursor.com/changelog/2-4)
- Cross-tool: Cursor also reads `~/.claude/skills/` and `.claude/skills/`, so skills shared with Claude Code can work in Cursor without duplication.

> **Credits:** These skills were adapted from [TÂCHES](https://github.com/glittercowboy/taches-cc-resources) prompt/command patterns and aligned with Cursor’s Agent Skills format.
