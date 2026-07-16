# Code Craft Skills

This repository collects reusable AI agent skills for day-to-day development
workflows.

The goal is to keep repeated prompting standards in one place: commit message
drafting, code logic improvement, unit test improvement, code style improvement,
and documentation improvement. Each skill keeps portable instructions in
`SKILL.md` and optional host metadata in `agents/openai.yaml`, so it can be
linked into agent-specific locations such as `.codex` or `.claude`.

## Skills

- `git-commit-message`: draft Conventional Commit messages from staged changes.
- `improve-code-logic`: find behavior risks and produce targeted fix plans.
- `improve-unit-tests`: improve risk-based test coverage, assertions, and
  maintainability.
- `improve-code-style`: improve naming, structure, simplicity, and consistency.
- `improve-documents`: improve README, AGENTS, docs, API docs, and code
  comments.

See `AGENTS.md` for repository conventions when adding or updating skills.
