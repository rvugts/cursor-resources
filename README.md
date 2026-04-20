# AI-chitect Cursor Resources

A comprehensive collection of Cursor rules, agent skills, MCP server configs, templates, and workflows for efficient vibe coding.

## Overview

This repository contains:

- **Cursor Skills** (`cursor-skills/`): Agent skills (`SKILL.md` files) for specification-driven development, code quality, security auditing, and meta-prompting
- **Cursor Rules** (`cursor-rules/`): Language-specific and workflow-specific rules
- **Cursor Settings** (`cursor-settings/`): `.cursorrules` and IDE/CLI configuration examples
- **Templates** (`templates/`): Project templates (spec, architecture, PR) and documentation templates
- **MCP Servers** (`mcp-servers/`): Configuration examples for Model Context Protocol servers
- **Prompts** (`prompts/`): Reusable prompts (SDD/TDD phase prompts, etc.)
- **Workflows** (`workflows/`): Step-by-step workflow guides
- **Cheatsheets** (`cheatsheets/`): Quick reference guides

## Quick Start

1. Copy `.cursorrules` from `cursor-settings/` to your project root
2. Copy relevant rule files from `cursor-rules/` to your project root in `.cursor/rules`
3. Copy relevant skills from `cursor-skills/` to `~/.cursor/skills/` (global) or `.cursor/skills/` (project-specific). See [`cursor-skills/README.md`](cursor-skills/README.md) for the full list, including `create-spec` and `create-tasks` for specification-driven development.

## Structure

See individual README files in each directory for detailed information.

## Credits

- **TÂCHES** - Original creator of the `create-prompt` and `run-prompt` patterns. The originals were designed for Claude Code and have been adapted into Cursor Agent Skills. See: [taches-cc-resources](https://github.com/glittercowboy/taches-cc-resources)
- **GitHub Skills (`create-spec`, `create-tasks`)** - Adapted from spec-driven development skills originally authored for GitHub Copilot / Claude Code and reformatted as Cursor Agent Skills in this repo.

## License

MIT License - see LICENSE file for details.
