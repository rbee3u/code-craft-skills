# Code Craft Skills

This repository collects reusable AI agent skills for my day-to-day development
workflow.

The goal is to keep repeated prompting standards in one place: commit message
drafting, code logic improvement, unit test improvement, code style improvement,
and documentation improvement. Each skill lives in its own top-level directory and
can be linked into agent-specific locations such as `.codex` or `.claude`.

## Skills

- `git-commit-message`: draft Conventional Commit-style messages from staged changes.
- `improve-code-logic`: identify correctness risks and produce fix plans.
- `improve-unit-tests`: improve test coverage, assertions, and maintainability.
- `improve-code-style`: improve naming, structure, simplicity, and consistency.
- `improve-documents`: improve README, AGENTS, docs, and code comments.

See `AGENTS.md` for repository conventions when adding or updating skills.
