---
name: release-notes
description: Draft user-facing release notes from supplied changes or a specified Git range. Use when preparing release notes or a changelog entry, not for general code review.
---

# Release Notes

Turn verified changes into concise notes that explain what users can do differently and whether they must take action.

## Workflow

1. Establish the release scope from the supplied changes or requested Git range. Ask for the range if needed; do not assume every recent commit belongs to the release.
2. Read the changes behind each candidate entry. Combine commits that implement one outcome and omit changes fully reverted within the release.
3. Group entries under **Breaking changes**, **Features**, and **Fixes**, in that order. Omit empty sections and internal refactors with no user-visible effect.
4. Write each bullet as a concrete user outcome. For breaking changes, explain the old behavior, new behavior, and required migration. Flag missing migration details rather than inventing them.
5. Check each claim against its source. Include supplied PR or issue links, preserve uncertainty, and use a version or date only when provided or verified.

## Writing Example

- Change: `fix: reset pagination when filters change`
- Release note: "Filtering results now returns you to the first page, avoiding an empty list when the previous page is outside the filtered results."

Use that level of specificity only when supported by the changes. Produce Markdown release notes; put unresolved questions after the draft. Do not publish a release unless requested.

## Optional Python Helper Demo

[scripts/group_changes.py](scripts/group_changes.py) contains a few print statements and comments describing how a helper could group changes. No dependencies or application setup are needed. Use `python3` if that is your interpreter command.

Run from the repository root with Python 3:

```sh
python instructions/skills/release-notes/scripts/group_changes.py
```

The script prints fictional groups and reads no Git history. It is optional: draft actual notes from the supplied evidence. A real helper could suggest groups, while the agent verifies user impact and migration details.
