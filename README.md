# 🧩 ai-agent-template

A small example of shared AI instructions, reusable skills, and native coding agents. No application setup is included.

- **Instructions** explain how we work here.
- **Roles** define responsibilities.
- **Skills** teach a task workflow.
- **Native agent files** configure each tool's agents and capabilities.

## Project structure

```text
AGENTS.md                         # Shared instruction router
CLAUDE.md / GEMINI.md             # Imports for other clients
.github/copilot-instructions.md   # Copilot instructions and PR review
.github/agents/                   # Native Copilot agents
.kiro/agents/                     # Native Kiro agents
.codex/agents/                    # Native Codex agents
.claude/agents/                   # Native Claude Code agents
roles/                            # Shared implementer and reviewer guidance
instructions/
  project-structure.md            # Repository context
  working-conventions.md          # Example team conventions
  agent-workflow.md               # Setup, coordination, and permissions
  skills/release-notes/
    SKILL.md                      # Release-notes workflow
    scripts/group_changes.py      # Tiny, print-only Python example
src/client/ / src/server/         # Empty application folders
docs/                             # Empty project documentation folder
```

## 🚀 Try it

Start with [agent setup and workflow](instructions/agent-workflow.md). In a session that supports delegation, ask:

> Use the implementer agent to create `docs/example.md` explaining instructions, roles, and skills in three short bullets. Then have a separate reviewer agent check it and return any findings for fixes.

## Agent support

Native agents are provided for **Codex, Claude Code, Copilot, and Kiro**. All four reuse the same role files; edit responsibilities once and configure capabilities separately for each client. Role instructions alone do not enforce permissions.

We keep [.github/copilot-instructions.md](.github/copilot-instructions.md) for automatic Copilot PR review, which is separate from our custom `reviewer` agent. Support for `AGENTS.md` varies between Copilot environments. See [GitHub's support matrix](https://docs.github.com/en/copilot/reference/custom-instructions-support).

## Skills and consistency

The [release-notes skill](instructions/skills/release-notes/SKILL.md) demonstrates a repeatable workflow and an optional Python helper. Its script prints fictional examples and needs no dependencies.

> [!NOTE]
> **Consistency:** Evaluate models on how reliably they follow your project's instructions, alongside coding ability. [Larger models do not automatically follow instructions better](https://arxiv.org/abs/2203.02155).
>
> For workflows that must run in a fixed order, consider explicitly running a Python script using [Pydantic AI](https://pydantic.dev/docs/ai/guides/multi-agent-applications/#programmatic-agent-hand-off) to call agents, [validate structured outputs](https://pydantic.dev/docs/ai/core-concepts/output/), and limit retries. The script must actually be invoked; mentioning it in Markdown does not enforce execution. This can make the workflow and output structure more consistent, but does not guarantee correct or identical answers.

## Centralized guidance for companies

Keep shared `instructions/`, `roles/`, and `skills/` files in a separate `company-ai-standards` repository. Use a GitHub Action to copy a selected version or tag into each project's local directories, such as `instructions/company/`, and open an automatic PR for review. Keep project-specific guidance separate, for example in `instructions/project/`.

Recommended flow: `company-ai-standards → version/tag → GitHub Action → automatic PR → project repository`.

Prefer local files over direct URL references: AI tools may handle external links and authentication differently. Point the project's instruction entry files to the local copies.

## More examples

For more examples, explore [Awesome Copilot](https://github.com/github/awesome-copilot). The separation of shared guidance and native agents is also inspired by [agent-setup](https://github.com/jonikanerva/agent-setup).
