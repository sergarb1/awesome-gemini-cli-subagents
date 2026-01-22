# GEMINI.md

This file provides guidance to Gemini CLI (gemini.ai/code) when working with code in this repository.

## Project Overview

This is a curated collection of Gemini CLI subagent definitions - specialized AI assistants for specific development tasks. Subagents are markdown files with YAML frontmatter that Gemini CLI can load and use.

## Repository Structure

```
agents/                  # All subagent definitions (.md files)
```

## Subagent File Format

Each subagent follows this template:

```yaml
---
name: agent-name
description: When this agent should be invoked (used by Gemini CLI for auto-selection)
tools: read_file, write_file, replace, run_shell_command, glob, search_file_content  # Comma-separated tool permissions
---

You are a [role description]...

[Agent-specific checklists, patterns, guidelines]

## Communication Protocol
[Inter-agent communication specs]

## Development Workflow
[Structured implementation phases]
```

### Tool Assignment by Role Type

- **Read-only** (reviewers, auditors): `read_file, search_file_content, glob`
- **Research** (analysts): `read_file, search_file_content, glob, web_fetch, google_web_search`
- **Code writers** (developers): `read_file, write_file, replace, run_shell_command, glob, search_file_content`
- **Documentation**: `read_file, write_file, replace, glob, search_file_content, web_fetch, google_web_search`

## Contributing a New Subagent

When adding a new agent, update these files:

1. **Main README.md** - Add link in appropriate category (alphabetical order)
2. **Agent .md file** - Create the actual agent definition

Format for main README: `- [**agent-name**](path/to/agent.md) - Brief description`

## Subagent Storage in Gemini CLI

| Type | Path | Scope |
|------|------|-------|
| Project | `.gemini/agents/` | Current project only |
| Global | `~/.gemini/agents/` | All projects |

Project subagents take precedence over global ones with the same name.
