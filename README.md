# ai-agent-template

A minimal example of organizing AI agent instructions and skills.

**Instructions** describe how we work here. **Skills** explain how to carry out a specific task.

```text
AGENTS.md                          # Routes tasks to relevant guidance
CLAUDE.md / GEMINI.md               # Imports the shared instructions
.github/copilot-instructions.md    # Copilot compatibility entry point
instructions/
  project-structure.md             # Repository context
  working-conventions.md           # Everyday project rules
  skills/release-notes/
    SKILL.md                       # Release-notes workflow
    scripts/group_changes.py       # Print-only Python demo
src/client/                        # Empty application folders
src/server/
docs/
```

Codex, Kiro, and Cursor use [AGENTS.md](AGENTS.md) directly. Claude Code, Gemini CLI, and Copilot have small compatibility entry files. See [agent compatibility](instructions/project-structure.md#agent-compatibility) for details. Skills are linked from the router; automatic discovery depends on the tool.

We keep [.github/copilot-instructions.md](.github/copilot-instructions.md) for Copilot code review and other Copilot environments where `AGENTS.md` support varies. It points to the shared guidance so project rules stay in one place. See [GitHub's support matrix](https://docs.github.com/en/copilot/reference/custom-instructions-support).

The [release-notes skill](instructions/skills/release-notes/SKILL.md) demonstrates a workflow with an optional Python helper. The script only prints examples. Application folders contain `.gitkeep` placeholders; no application setup is included.

## More examples and tools

Use [Awesome Copilot](https://github.com/github/awesome-copilot) for inspiration when creating instruction files, skills, and custom agents. It also includes hooks, workflows, and plugins. Adapt the examples to your project and your chosen agent's supported formats.
