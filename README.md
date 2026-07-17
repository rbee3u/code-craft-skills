# Code Craft Skills

Reusable AI agent skills for day-to-day development workflows. Each skill keeps
portable instructions in `SKILL.md` and optional host metadata in
`agents/openai.yaml`, so it can be linked into agent-specific locations such as
`.codex` or `.claude`.

These skills intentionally encode personal preferences — simplicity first,
consistency, restraint in abstractions, comments, and tests — rather than
generic best practices.

## Skills

- `git-commit-message`: draft Conventional Commit messages from staged changes.
- `improve-code-logic`: find behavior risks and produce targeted fix plans.
- `improve-code-style`: improve naming, structure, simplicity, and consistency.
- `improve-unit-tests`: improve risk-based test coverage, assertions, and
  maintainability.
- `improve-documents`: improve README, AGENTS, docs, and code comments.

See `AGENTS.md` for repository conventions when adding or updating skills.
