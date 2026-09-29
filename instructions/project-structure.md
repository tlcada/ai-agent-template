---
description: "Example repository layout and application boundaries"
---

# Project Structure

`ai-agent-template` demonstrates three layers: an instruction router, topic-specific conventions, and a skill that uses executable code.

## Layout

```text
AGENTS.md                          # Routes tasks to relevant instructions
README.md                          # Explains how to use the template
CLAUDE.md                          # Imports AGENTS.md for Claude Code compatibility
GEMINI.md                          # Imports AGENTS.md for Gemini CLI
.github/copilot-instructions.md    # Copilot entry point
instructions/
  project-structure.md             # Repository context and boundaries
  working-conventions.md           # Examples of everyday project rules
  skills/
    release-notes/
      SKILL.md                     # Workflow and helper usage
      scripts/
        group_changes.py           # Print-only grouping demo with explanatory comments
src/
  client/                          # Browser UI
  server/                          # API and server logic
tests/                             # Automated tests
docs/                              # Project documentation
```

The four application and documentation folders contain only `.gitkeep` files. Remove each placeholder when the folder contains real files. There is no application manifest, framework, test runner, or build configuration yet.

## Agent Compatibility

Keep shared rules in `AGENTS.md`. Entry files only import or point to it; avoid maintaining copies of the same rules.

| Tool | How it reads this template |
| --- | --- |
| [Codex](https://learn.chatgpt.com/docs/agent-configuration/agents-md) | Discovers the root `AGENTS.md`; no `.codex/` folder is needed for these instructions. |
| [Kiro](https://kiro.dev/docs/steering/) | Automatically loads the root `AGENTS.md`; a steering file that only redirects there is unnecessary. Custom agents may require explicit resource configuration. |
| [Cursor Agent](https://cursor.com/docs/rules) | Reads the root `AGENTS.md`; no `.cursor/` rules are needed for this example. |
| [GitHub Copilot](https://docs.github.com/en/copilot/reference/custom-instructions-support) | Support for `AGENTS.md` varies by environment. The small `.github/copilot-instructions.md` points to shared guidance. |
| [Claude Code](https://code.claude.com/docs/en/memory#agentsmd) | Recent versions can read `AGENTS.md` directly. `CLAUDE.md` imports it for compatibility with sessions that use Claude-specific instruction files. |
| [Gemini CLI](https://geminicli.com/docs/cli/gemini-md/) | `GEMINI.md` imports the shared instructions with `@./AGENTS.md`. |

These describe instruction entry points, not automatic skill installation. The example skill is routed through `AGENTS.md`; native skill discovery and custom-agent settings depend on the tool. Confirm loaded instructions in your chosen client after setup.

## Application Boundaries

- Keep browser code in `src/client/` and server-only logic in `src/server/`.
- Extract shared contracts and utilities when needed. Keep credentials and database clients out of browser imports.
- Group code by feature as the application grows; add directories when needed.
- Keep project documentation in `docs/` and automated tests in `tests/`.

## Customize for Your Project

Replace this example context with the product's purpose, chosen stack, supported runtimes, setup commands, and verification commands. Document security boundaries and deployment details when implemented.

Use fictional names and sanitized configuration in public examples. Keep architecture and repository context here, everyday rules in [working conventions](working-conventions.md), and task-specific workflows in skills.
