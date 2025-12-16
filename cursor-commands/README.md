# Cursor Slash Commands

Custom AI agents invoked with `/command-name` in Cursor Composer.

## Installation

### Global Commands (Recommended)

Available in all projects:

```bash
mkdir -p ~/.cursor/commands
cp *.md ~/.cursor/commands/
```

### Project-Specific Commands

For project-only commands:

```bash
mkdir -p .cursor/commands
cp refactor-python.md .cursor/commands/
```

## Available Commands

### Code Quality

- `/refactor-python` - Refactor Python code (DRY, 25-line functions, type hints)
- `/audit-security` - Review code against OWASP Top 10

### Meta-Prompting (Advanced)

- `/create-prompt` - Interview mode to build perfect prompts
- `/run-prompt` - Execute previously created prompt files

## Usage

In Cursor Composer (`Cmd/Ctrl+I`):

```
/refactor-python @my_module.py
```

With additional context:

```
/audit-security @api/auth.py Check for SQL injection and XSS
```
