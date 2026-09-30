# Project Structure

`ai-agent-template` teaches how to organize project guidance and configure a small implementation-and-review workflow.

## Where Things Belong

| Location | Purpose |
| --- | --- |
| [AGENTS.md](../AGENTS.md) | Shared task router |
| [Working conventions](working-conventions.md) | Everyday team rules |
| [roles/](../roles/) | Shared responsibilities, inputs, and outputs |
| [.codex/agents/](../.codex/agents/), [.claude/agents/](../.claude/agents/), [.github/agents/](../.github/agents/), [.kiro/agents/](../.kiro/agents/) | Native agent definitions and capability settings |
| [Release-notes skill](skills/release-notes/SKILL.md) | Task workflow with a tiny illustrative Python helper |
| [Agent guide](agent-workflow.md) | Setup, workflow, and permission boundaries |
| `src/client/` and `src/server/` | Empty browser and server application folders |
| `docs/` | Project documentation |

`CLAUDE.md`, `GEMINI.md`, and `.github/copilot-instructions.md` connect clients to the shared guidance. See [agent setup](agent-workflow.md#start-a-session) and [other clients](agent-workflow.md#other-clients).

## Application Boundaries

- Keep browser code in `src/client/` and server-only logic in `src/server/`.
- Keep credentials and database clients out of browser imports.
- Group code by feature as the application grows; add shared utilities and test folders when needed.
- Remove a `.gitkeep` when its folder contains real files.

## Adapt to a Real Project

Replace this example context with the product's purpose, chosen stack, setup commands, and verification commands. No application manifest, framework, test runner, or build configuration exists yet.

Keep ordinary team decisions in [working conventions](working-conventions.md), task workflows in skills, and tool-specific capabilities in native agent files. Use fictional names and sanitized data in public examples.
