# ai-agent-template

This repository demonstrates a small, modular set of instructions for AI coding agents. Application folders contain only `.gitkeep` placeholders; no application or build pipeline is configured.

## Task routing

Read [project structure](instructions/project-structure.md) before making changes, then load only the guidance relevant to the task.

| Task | Guidance |
| --- | --- |
| Editing code or documentation | [Working conventions](instructions/working-conventions.md) |
| Drafting release notes from changes | [Release-notes skill](instructions/skills/release-notes/SKILL.md) |

Keep this file short. Add topic-specific guidance under `instructions/` and link it here when the project needs it.

## Verification

For documentation changes, check local links and referenced paths. For application changes, use the project's configured checks once they exist. Report checks run and any limitations; do not invent commands or claim unrun tests passed.
