---
name: git-commit-message
description: Draft a Conventional Commit message from staged Git changes. Use when the user asks to generate, suggest, write, or prepare a commit message.
---

# Git Commit Message

Draft a ready-to-use Conventional Commit message from staged changes only.
Never run `git commit` unless the user explicitly asks after seeing the
proposal.

## Workflow

1. Inspect `git status --short` and `git diff --staged`.
2. If the staged diff is empty, stop and say there are no staged changes.
3. Note unstaged or untracked paths only as excluded context.
4. Infer the type and optional scope from the staged behavior and project
   conventions.
5. Base the subject and body only on the staged diff.

## Message Rules

- Write in English and use Conventional Commit style, such as `feat:`,
  `fix:`, `docs:`, `refactor:`, `test:`, or `chore:`.
- Use an imperative subject under 72 characters when practical.
- Add a scope only when the staged diff has a clear focused area.
- Add a 1-3 line body only when the diff needs why, risk, or context.
- Never mention unstaged changes, tooling internals, or uncertain intent inside
  the message.

## Output

Return the message first in a Markdown code block, then say:
"This is only a proposed commit message; no `git commit` has been run. I will
wait for explicit approval before committing."

If there are no staged changes, report that directly and do not draft a
placeholder message.
