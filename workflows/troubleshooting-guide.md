# Troubleshooting Guide

Common issues and solutions when working with Cursor AI.

## Issue: AI Not Understanding Context

### Symptoms
- AI suggests irrelevant code
- AI doesn't use existing patterns
- AI ignores project structure

### Solutions
1. Check `.cursorrules` is in project root
2. Verify `.cursorignore` isn't excluding important files
3. Provide more context in prompts
4. Reference specific files in prompts
5. Use @ mentions for file context

## Issue: Poor Code Suggestions

### Symptoms
- Code doesn't follow project conventions
- Suggests outdated patterns
- Ignores best practices

### Solutions
1. Update `.cursorrules` with specific guidelines
2. Add language-specific rules from `cursor-rules/`
3. Provide examples of desired code style
4. Use more specific prompts
5. Review and refine rules

## Issue: AI Not Following Workflows

### Symptoms
- Skips testing
- Doesn't write documentation
- Ignores specification

### Solutions
1. Reference workflow files in prompts
2. Use workflow-specific prompts
3. Break tasks into smaller steps
4. Explicitly request each phase
5. Use checklists

## Issue: Context Window Limitations

### Symptoms
- AI loses track of conversation
- Doesn't remember earlier decisions
- Repeats questions

### Solutions
1. Break large tasks into smaller ones
2. Use implementation status tracking
3. Reference previous decisions explicitly
4. Use summaries for long conversations
5. Start fresh conversations for new features

## Issue: Inconsistent Behavior

### Symptoms
- Different suggestions for similar tasks
- Contradictory advice
- Unpredictable responses

### Solutions
1. Use consistent prompt templates
2. Reference established patterns
3. Use command files from `cursor-commands/`
4. Maintain project conventions
5. Review and update rules regularly

## Getting Help

1. Check relevant workflow guides
2. Consult cheatsheets
3. Use meta-prompting to improve prompts
4. Refine `.cursorrules` and language-specific cursor rules for your needs


