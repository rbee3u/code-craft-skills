# Agent Instructions

This repository stores reusable AI agent skills. Each top-level skill directory
is portable across agent hosts, with host-specific metadata kept separate from
the core instructions in `SKILL.md`.

## Content Philosophy

Skills capture personal preferences, not industry consensus. Keep only rules
that resolve real ambiguity: choices a capable model might make differently if
left unsaid, such as Occam's razor, consistency over personal taste, or
restraint in abstractions, comments, and tests. Do not restate generic
methodology or best practices a capable model already follows.

## Repository Structure

- One top-level directory per skill, named in lowercase hyphen-case, exactly
  matching the `name` field in `SKILL.md`.
- Portable instructions live in `<skill-name>/SKILL.md`; OpenAI/Codex UI
  metadata lives in `<skill-name>/agents/openai.yaml`.
- Add `scripts/`, `references/`, or `assets/` only when they directly support
  the skill. Do not add auxiliary docs inside a skill directory.
- Keep `CLAUDE.md` as a symlink to this file, not a separate copy.

## Skill Format

`SKILL.md` frontmatter contains only `name` and `description` (a clear trigger
for when the skill should be used). Write the body in English as short
imperative rules; prefer sections such as a purpose statement, `Workflow`,
`Priorities`, `Negative Constraints`, and `Output Format` when they fit.

In `agents/openai.yaml`, keep only `interface.display_name` and
`interface.short_description` synchronized with `SKILL.md`. Do not add optional
fields unless the user explicitly asks.

## Naming

Prefer `improve-*` for skills that inspect something and propose concrete
improvements. Avoid `review-*` unless the skill is intentionally read-only.

## Workflow And Hygiene

- Validate every changed skill before reporting completion, using the
  skill-creator tooling of the active agent environment (for example
  `~/.codex/skills/.system/skill-creator/scripts/quick_validate.py`, which
  requires PyYAML).
- Do not commit changes unless the user explicitly asks.
- Preserve user changes and staged state. Do not reset, checkout, or revert
  files unless the user explicitly requests that operation.
