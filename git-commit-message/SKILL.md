---
name: git-commit-message
description: Draft a Conventional Commit-style message from the staged Git diff. Use when the user asks to generate, suggest, write, or prepare a commit message for staged changes.
---

# Git Commit Message

Draft a ready-to-use message from staged changes only. Do not run `git commit` unless the user explicitly approves after seeing the proposal.

## Workflow

1. Inspect `git diff --staged`; if empty, stop.
2. Check unstaged changes with `git diff --quiet` or `git status --short`.
3. If present, tell the user they are excluded.
4. Base the message only on the staged diff.

## Message Rules

- Write in English and use Conventional Commit style, such as `feat:`, `fix:`, `docs:`, `refactor:`, `test:`, or `chore:`.
- Add a scope only for a clear focused area.
- Add a 1-3 line body only for useful why/context.
- Never mention unstaged changes inside the message.

## Output

Return the message first in a Markdown code block, then say:
"This is only a proposed commit message; no `git commit` has been run. I will wait for explicit approval before committing."
