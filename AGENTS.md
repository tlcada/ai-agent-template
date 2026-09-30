# ai-agent-template

This is an example of AI instructions, roles, skills, and native agents. Application folders contain only `.gitkeep` placeholders; there is no application or build pipeline.

## Task routing

Read [project structure](instructions/project-structure.md) before making changes, then load only the guidance relevant to the task.

| Task | Guidance |
| --- | --- |
| Editing code or documentation | [Working conventions](instructions/working-conventions.md) |
| Implementing a requested change | [Implementer role](roles/implementer.md) |
| Reviewing supplied changes | [Reviewer role](roles/reviewer.md) |
| Setting up or coordinating separate agents | [Agent setup and workflow](instructions/agent-workflow.md) |
| Drafting release notes from changes | [Release-notes skill](instructions/skills/release-notes/SKILL.md) |

Use the role matching the task. Use separate agents when requested; otherwise a single agent can follow the relevant role. Role Markdown describes behavior, while native configuration and the active client control capabilities.

Keep shared rules here or in `instructions/`. Native agent files should load the shared guidance rather than repeat it.

## Verification

Check local links and referenced paths for documentation changes. Validate native configuration syntax when changing it. Use application checks only once configured. Report checks run and any limitations; do not claim unrun tests or agent sessions passed.
