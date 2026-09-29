---
description: "Example everyday project conventions to adapt for your team"
---

# Working Conventions

Use this file for **how we work here**: decisions that apply across ordinary tasks. The examples below are a starting point. Replace or extend them with your team's actual conventions.

## Example: Code Changes

- Follow the naming and organization of the surrounding code. For example, keep a new component beside related components instead of creating a new top-level folder.
- Keep changes focused on the requested behavior. Explain any necessary changes to shared interfaces.

## Example: Documentation

- Update setup instructions when commands or prerequisites change.
- Use fictional data in public examples, such as `example-app` and `user@example.com`; keep private project names and credentials out of documentation.

## Example: Verification

- For a behavior fix, check the failing scenario and add a focused regression test when a test setup exists.
- For documentation edits, check local links and referenced commands. Report what was checked and what could not be verified.

## Add Your Own Conventions

Useful additions include file naming, error-response formats, UI terminology, and where tests belong. Write concrete rules based on actual project decisions. Document real commands only after configuring them.

Keep this file small. Move larger topics into their own instruction files and link them from `AGENTS.md`. Put a task-specific workflow, such as drafting release notes, in a skill.
