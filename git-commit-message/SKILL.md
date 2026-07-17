---
name: git-commit-message
description: Draft a Conventional Commit message from staged Git changes. Use when the user asks to generate, suggest, write, or prepare a commit message.
---

# Git Commit Message

Draft a ready-to-use commit message from staged changes only. Never run
`git commit` unless the user explicitly asks after seeing the proposal.

## Workflow

1. Inspect `git status --short` and `git diff --staged`.
2. If the staged diff is empty, stop and say there are no staged changes; do
   not draft a placeholder message.
3. Base the message only on the staged diff; never mention unstaged changes.

## Message Rules

- Write in English using Conventional Commit style, such as `feat:`, `fix:`,
  `docs:`, `refactor:`, `test:`, or `chore:`.
- Use an imperative subject under 72 characters when practical.
- Add a scope only when the staged diff has a clear focused area.
- Add a 1-3 line body only when the diff needs why, risk, or context.

## Output

Return the message in a Markdown code block, then state that this is only a
proposal and no `git commit` has been run.
