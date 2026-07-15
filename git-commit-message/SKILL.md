---
name: git-commit-message
description: Draft a Conventional Commit-style message from the current staged Git diff. Use when the user asks to generate, suggest, write, or prepare a commit message for staged changes.
---

# Git Commit Message

Draft a directly usable commit message from staged changes only. Do not run `git commit`; this skill only proposes commit text unless the user separately approves committing after the proposal.

## Workflow

1. Run `git diff --staged`.
2. If the staged diff is empty, stop and tell the user there is no staged diff to use.
3. Check for unstaged changes with `git diff --quiet` or `git status --short`.
4. If unstaged changes exist, tell the user in Chinese that they are not included in the commit message basis.
5. Generate the commit message only from `git diff --staged`.

## Message Rules

- Write the commit message in English.
- Use Conventional Commits, for example `feat:`, `fix:`, `docs:`, `refactor:`, `test:`, or `chore:`.
- Add a scope only when the staged diff has a clear focused area.
- Add a 1-3 line body only when it adds useful why/context.
- Do not mention unstaged changes in the commit message itself.

## Output

Return the suggested commit message first in a Markdown code block, followed by:
`当前仅生成提交内容，尚未执行 git commit；如需继续提交，必须等待用户明确批准。`
