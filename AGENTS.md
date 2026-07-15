# Agent Instructions

This repository stores reusable AI agent skills. Each top-level skill directory is
intended to be portable across agent hosts, with optional host-specific metadata kept
separate from the core skill instructions.

## Repository Structure

- Put each skill in its own top-level directory named after the skill.
- Use lowercase hyphen-case for skill names.
- Keep the directory name and the `name` field in `SKILL.md` exactly aligned.
- Put portable instructions in `<skill-name>/SKILL.md`.
- Put OpenAI/Codex UI metadata in `<skill-name>/agents/openai.yaml`.
- Add `scripts/`, `references/`, or `assets/` only when they directly support the
  skill. Do not add auxiliary docs inside a skill directory.
- Keep `CLAUDE.md` as a symlink to this file, not a separate copy.

## Skill Format

`SKILL.md` must have YAML frontmatter with only:

```yaml
---
name: skill-name
description: Clear trigger description for when the skill should be used.
---
```

The Markdown body should be concise and actionable. Prefer these sections when they
fit the skill:

- A short purpose statement.
- `Workflow`
- `Priorities` or `Improvement Priorities`
- `Negative Constraints`
- `Output Format`

Write skill instructions in English unless the user explicitly asks otherwise.
Favor imperative guidance and concrete decision rules over broad explanation.

## OpenAI Metadata

For `agents/openai.yaml`, keep the values synchronized with `SKILL.md`:

- `interface.display_name`: human-readable title.
- `interface.short_description`: short UI description.
- `interface.default_prompt`: short prompt that explicitly mentions `$skill-name`.

Do not add optional fields such as icons, brand colors, dependencies, or policy unless
the user explicitly asks for them.

## Creation And Update Workflow

When creating a new skill:

1. Clarify the intended repeated workflow from the user's examples.
2. Choose a concise hyphen-case name.
3. Prefer the local `skill-creator` scripts when available.
4. Write the portable behavior in `SKILL.md`.
5. Add or update `agents/openai.yaml`.
6. Validate the changed skill.

Useful local commands in this workspace:

```bash
python3 /home/codex/.codex/skills/.system/skill-creator/scripts/init_skill.py <skill-name> --path /work
/tmp/codex-skill-validate-venv/bin/python /home/codex/.codex/skills/.system/skill-creator/scripts/quick_validate.py /work/<skill-name>
```

If those paths are unavailable, use the equivalent skill-creator tooling from the
active agent environment.

## Current Naming Pattern

- `git-commit-message`: draft Conventional Commit-style messages from staged diffs.
- `improve-code-logic`: find correctness risks and produce fix plans.
- `improve-unit-tests`: improve unit test coverage, assertions, and maintainability.
- `improve-code-style`: improve naming, structure, simplicity, and maintainability.
- `improve-documents`: improve docs and code comments.

Prefer `improve-*` for skills that inspect something and propose concrete
improvements. Avoid `review-*` unless the skill is intentionally read-only.

## Repository Hygiene

- Do not create a root `README.md` unless the user explicitly asks for it.
- Do not commit changes unless the user explicitly asks.
- Preserve user changes and staged state. Do not reset, checkout, or revert files
  unless the user explicitly requests that operation.
- Use `rg` or `rg --files` for searching when available.
- Validate every changed skill before reporting completion.
