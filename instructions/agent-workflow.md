# Agent Setup and Workflow

Shared [roles](../roles/) define responsibilities and handoffs once. Native files configure each client's agents and capabilities. Keep review criteria in the shared reviewer role; change tools and models in the native definitions.

## Start a Session

Open the repository root in a client that supports the formats below. Start a new session after adding these files and confirm that `implementer` and `reviewer` are available. Report unavailable definitions instead of silently substituting another agent.

| Client | Project definitions | Capability defaults |
| --- | --- | --- |
| Codex | [.codex/agents/](../.codex/agents/) | Implementer: workspace writes. Reviewer: read-only filesystem sandbox, no approval escalation. |
| Claude Code | [.claude/agents/](../.claude/agents/) | Implementer: read, search, edit, write, shell. Reviewer: only Read, Grep, Glob. |
| GitHub Copilot | [.github/agents/](../.github/agents/) | Implementer: read, search, edit, execute. Reviewer: only read and search. |
| Kiro | [.kiro/agents/](../.kiro/agents/) | Implementer: read, write, shell. Reviewer: only the read category, including search. |

Models are unpinned: clients use their session, subagent, or default model settings. All definitions load shared guidance; Kiro references the role as a prompt file and explicitly loads `AGENTS.md` as a resource.

- **Codex / Claude:** Ask the primary agent to delegate to the named agents. See [Codex subagents](https://learn.chatgpt.com/docs/agent-configuration/subagents) and [Claude Code subagents](https://code.claude.com/docs/en/sub-agents).
- **Copilot:** Select the custom agent in a supported IDE, or request it in Copilot CLI. Client support differs; VS Code handoff buttons are not portable to the cloud agent, so this example omits them. See [agent configuration](https://docs.github.com/en/copilot/reference/custom-agents-configuration) and [CLI invocation](https://docs.github.com/en/copilot/how-tos/copilot-cli/use-copilot-cli/invoke-custom-agents).
- **Kiro:** These profiles target IDE 1.x / CLI 3.x. Select an agent locally or ask the primary agent to delegate to it. Web can delegate to committed project agents; Mobile does not load custom agents. See [Kiro custom agents](https://kiro.dev/docs/custom-agents/) and [delegation](https://kiro.dev/docs/custom-agents/subagents/).

## Implementation and Review

In a general session with delegation available, ask the primary agent:

> Use implementer to [describe the change and acceptance criteria], then reviewer to inspect the actual changes. Follow instructions/agent-workflow.md for the handoff and fixes.

1. **Scope:** The primary agent records the request, acceptance criteria, relevant paths, and pre-existing changes.
2. **Implement:** Give that scope to `implementer`. Wait for its changes and verification results before review.
3. **Review:** Give `reviewer` the original request, scope, actual diff including new files, and check results. It reads the actual files too. The Claude, Copilot, and Kiro reviewers have no shell, so supply their diff explicitly.
4. **Fix:** Return actionable findings to `implementer`, then review the updated changes. Limit this example workflow to two review passes; report any remaining issues instead of looping indefinitely.
5. **Report:** The primary agent summarizes changes, findings addressed, checks run, and remaining gaps.

The specialist agents do not coordinate the workflow themselves. When selecting them manually, pass the handoff between sessions yourself. The template does not start agents or configure automatic PR review.

Use one writer at a time in the shared checkout. Agent context is separate: pass evidence explicitly and do not assume access to another agent's conversation. A review with missing evidence is incomplete, even if it reports no findings.

For a small task, one agent can follow the role files directly. Describe that as a self-review, not an independent agent review.

## Permission Boundaries

Writing "read-only" in a role file is behavioral guidance. Native tools and sandbox settings constrain capabilities when loaded by the client; implementer tools remain subject to active permission rules.

The Codex reviewer pairs `read-only` with `approval_policy = "never"`; blocked checks should stay blocked. Session overrides, pre-approved command rules, and inherited MCP tools still need inspection: a filesystem sandbox does not restrict external service writes. These files configure local Codex, not hosted ChatGPT chats. See [Codex configuration](https://learn.chatgpt.com/docs/config-file/config-reference).

The Claude, Copilot, and Kiro reviewers expose read/search tools only. They can inspect test code and supplied results, but cannot run tests themselves. Adding a shell to run tests also introduces write capability.

Kiro's `tools` controls availability; `allowedTools` controls which available tools can run without approval. Both profiles pre-approve only reads and disable MCP configuration and power imports. Prompt paths resolve relative to the agent JSON; `file://AGENTS.md` is a workspace resource. See [Kiro configuration](https://kiro.dev/docs/custom-agents/configuration-reference/).

Before relying on these boundaries, check the loaded definition and effective permissions in your client. Keep mutating integrations away from review agents. This template does not configure credentials, global settings, or external services.

## Copilot PR Review

The custom `reviewer` is an agent you select or invoke. GitHub's automatic Copilot PR review is a separate feature; adding `reviewer.agent.md` does not configure it. Keep [.github/copilot-instructions.md](../.github/copilot-instructions.md) as its instruction entry point. See [instruction support](https://docs.github.com/en/copilot/reference/custom-instructions-support).

## Other Clients

[Cursor](https://cursor.com/docs/rules) can use the root `AGENTS.md`; [Gemini CLI](https://geminicli.com/docs/cli/gemini-md/) uses the [GEMINI.md](../GEMINI.md) import. This template supplies shared guidance for them, without native agent definitions.

Keep only the native definitions your project uses. Retain shared roles when supporting multiple clients; a project using one client can inline the role into its native definition.

The [release-notes skill](skills/release-notes/SKILL.md) is linked from `AGENTS.md`. Its location demonstrates explicit routing; this template does not install it into every client's automatic skill-discovery directory.
