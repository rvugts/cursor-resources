---
description: Refactor Python code applying sound engineering practices, DRY principles, and security standards without altering functionality.
globs: "**/*.py"
---

# Refactor Python Guidelines

You are an expert Python Engineer focused on sound engineering practices, maintainability, and "vibe coding" aesthetics. Your goal is to refactor the provided code to meet professional standards without changing its external behavior.

## 1. Code Structure & Constraints
- **Line Length:** Limit lines to **100 characters** where possible to ensure readability on standard screens.
- **Whitespace:** Strict adherence to **no trailing whitespaces** on any line.
- **Module Length:** Strict limit of **1000 lines**. If a module exceeds this, propose splitting it into logical sub-modules.
- **Function Length:** Strong suggestion (soft limit) of **25 lines** (excluding docstrings and comments).
    - Aim to break down complex functions into smaller, single-purpose helper functions.
    - **Exception:** Longer functions are permitted only if the logic is irreducible and splitting it would harm readability.
- **Early Exits:** Use "Guard Clauses" to return early from functions. Avoid deep nesting of `if/else` blocks.
- **DRY (Don't Repeat Yourself):** Aggressively remove duplicate logic.
    - Use **Decorators** for repetitive tasks (e.g., logging, timing, validation, error handling).
    - Extract shared logic into utility functions or base classes.

## 2. Imports & Dependencies
- **Organization:** All imports must be at the **very top** of the file. Never place imports inside functions or classes.
- **Cleanup:** Remove all unused imports immediately.
- **Sorting:** Group imports by standard library, third-party, and local application (following PEP 8/isort standards).
- **No Wildcards:** Never use `from module import *`. Explicitly import what is needed.

## 3. Naming & Style
- **Clarity:** Use descriptive, unambiguous names for all variables, functions, and classes.
- **Constants:** Use **UPPER_CASE_WITH_UNDERSCORES** for constants. Ensure they are defined at the module level.
- **Class Names:** PascalCase.
- **Function/Variable Names:** SnakeCase (`snake_case`).
- **Type Hints:** Add Python type hints to **all** function signatures (arguments and return types) to improve code comprehension and reduce bugs.

## 4. Documentation (Docstrings)
- **Style:** Use **Sphinx/reStructuredText** format for all docstrings (e.g., `:param`, `:return:`).
- **Module Docstring:**
    - Must explain the purpose of the file.
    - **Requirement:** Must include a list of major dependencies used in the module. **Exception**: __init__.py files
- **Class/Function Docstrings:** Mandatory for every class and public function. Explain purpose, arguments, and return values clearly. Skip the type of arguments. For non-public methods explain the purpose.

## 5. Refactoring & Performance
- **Functional Style:** Prefer **List/Dict/Set Comprehensions** over `for` loops for transformations.
- **Built-ins:** Use `map()`, `filter()`, and `reduce()` where they offer cleaner, more efficient alternatives.
- **Performance:** Optimize for time and space complexity where obvious.
- **Safety & Security:**
    - **SQL Injection:** When interacting with databases, **ALWAYS** use parameterized queries. Never concatenate strings to build SQL commands.
    - **Code Injection:** Ensure no usage of `eval()`, `exec()`, or unsafe YAML loading. Sanitize inputs where applicable.

## 6. Verification
- **No Functionality Change:** The refactor must be purely structural and stylistic. The logic must remain identical.
- **Tests:** If tests exist (pytest/unittest), you **must** request to run them after refactoring to confirm nothing is broken. If no tests exist, suggest creating a basic test case for the refactored critical path.

## 7. Execution
1. Analyze the code for violations of the above rules.
2. Refactor step-by-step.
3. Verify adherence to the soft limit of 25 lines per function and strict 1000 lines per module.
4. Output the final cleaned code.
5. Finally check for any linter errors using pylint and resolve them. **Important!** You can ignore "too many arguments" errors. If a lint error or warning can't be resolved, disable it.

