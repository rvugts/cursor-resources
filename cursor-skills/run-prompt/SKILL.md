---
name: run-prompt
description: Delegate one or more prompts to fresh sub-task contexts with parallel or sequential execution
disable-model-invocation: true
---

<context>
Git status: Check with `git status --short`
Recent prompts: Check with `ls -t ./prompts/*.md | head -5`
</context>

<objective>
Execute one or more prompts from `./prompts/` as delegated sub-tasks with fresh context. Supports single prompt execution and sequential execution of multiple prompts.
</objective>

<input>
The user will specify which prompt(s) to run, which can be:

**Single prompt:**

- Empty (no arguments): Run the most recently created prompt (default behavior)
- A prompt number (e.g., "001", "5", "42")
- A partial filename (e.g., "user-auth", "dashboard")

**Multiple prompts:**

- Multiple numbers (e.g., "005 006 007")
- Multiple prompts are always executed sequentially
</input>

<process>
<step1_parse_arguments>
Parse the user's input to extract prompt numbers/names.

<examples>
- "005" → Single prompt: 005
- "005 006 007" → Multiple prompts: [005, 006, 007], strategy: sequential
</examples>
</step1_parse_arguments>

<step2_resolve_files>
For each prompt number/name:

- If empty or "last": Find the most recent file with `ls -t ./prompts/*.md | head -1`
- If a number: Find file matching that zero-padded number (e.g., "5" matches "005-*.md", "42" matches "042-*.md")
- If text: Find files containing that string in the filename

<matching_rules>

- If exactly one match found: Use that file
- If multiple matches found: List them and ask user to choose
- If no matches found: Report error and list available prompts
</matching_rules>
</step2_resolve_files>

<step3_execute>
<single_prompt>

1. Read the complete contents of the prompt file
2. Create a new Composer agent/chat and paste the prompt contents
3. Wait for completion
4. Archive prompt to `./prompts/completed/` with metadata
5. Commit all work:
   - Stage files modified with `git add [file]` (never `git add .`)
   - Determine appropriate commit type based on changes (fix|feat|refactor|style|docs|test|chore)
   - Commit with format: `[type]: [description]` (lowercase, specific, concise)
6. Return results
</single_prompt>

<sequential_execution>

1. Read first prompt file
2. Create Composer agent/chat with first prompt
3. Wait for completion
4. Archive first prompt
5. Read second prompt file
6. Create Composer agent/chat with second prompt
7. Wait for completion
8. Archive second prompt
9. Repeat for remaining prompts
10. Commit all work:
    - Stage files modified with `git add [file]` (never `git add .`)
    - Determine appropriate commit type based on changes (fix|feat|refactor|style|docs|test|chore)
    - Commit with format: `[type]: [description]` (lowercase, specific, concise)
11. Return consolidated results
</sequential_execution>
</step3_execute>
</process>

<context_strategy>
By delegating to a sub-task (new Composer agent/chat), the actual implementation work happens in fresh context while the main conversation stays lean for orchestration and iteration.
</context_strategy>

<o>
<single_prompt_output>
✓ Executed: ./prompts/005-implement-feature.md
✓ Archived to: ./prompts/completed/005-implement-feature.md

<results>
[Summary of what the sub-task accomplished]
</results>
</single_prompt_output>

<sequential_output>
✓ Executed SEQUENTIALLY:

1. ./prompts/005-setup-database.md → Success
2. ./prompts/006-create-migrations.md → Success
3. ./prompts/007-seed-data.md → Success

✓ All archived to ./prompts/completed/

<results>
[Consolidated summary showing progression through each step]
</results>
</sequential_output>
</o>

<critical_notes>

- For sequential execution: Execute each prompt one at a time in order
- Archive prompts only after successful completion
- If any prompt fails, stop sequential execution and report error
- Provide clear, consolidated results for multiple prompt execution
- Always use `git add [specific-file]` - never `git add .`
</critical_notes>
