---
name: improve-documents
description: Improve documentation and code comments for accuracy, clarity, usefulness, scope, and implementation consistency. Use when the user asks to assess or improve README.md, AGENTS.md, docs, API docs, module/library/component docs, or code comments.
---

# Improve Documents

Improve docs and comments as engineering guidance. Keep useful guidance accurate and actionable; remove or avoid noise.

## Workflow

1. Determine scope from the request, changed files, READMEs, AGENTS files, docs, API docs, or comments.
2. Read enough related code, config, scripts, and tests to verify actual behavior.
3. Identify the audience: users, contributors, operators, API consumers, or coding agents.
4. Check whether content explains the right things at the right level: purpose, constraints, usage, setup, commands, decisions, and caveats.
5. Preserve good docs and comments; do not rewrite for stylistic uniformity.
6. Report stale, misleading, redundant, missing, over-detailed, or poorly scoped content with concrete fixes.
7. Do not change unrelated logic, names, formatting, or tests unless asked.

## Documentation Priorities

- Match current implementation, commands, config, layout, behavior, and supported workflows.
- READMEs explain what the project is, setup, run/test commands, and where deeper docs live.
- AGENTS files give concise agent instructions: layout, build/test/lint commands, conventions, constraints, and workflow expectations.
- Docs have a clear audience, scope, and source-of-truth relationship.
- Examples, commands, environment variables, paths, and API references are accurate and runnable where practical.
- Long docs scan well with clear headings, stable terms, and focused sections.
- Cross-references point to canonical locations and avoid circular or stale guidance.
- Explain why, when, and how; do not restate code line by line.
- Missing docs matter only when they block use, contribution, operation, review, or maintenance.

## Comment Priorities

- Add or keep comments only when they provide clear value.
- Comment public APIs when the language, framework, or project convention expects it.
- Explain responsibilities, constraints, preconditions, caller obligations, observable differences, compatibility, protocols, workarounds, or surprising behavior.
- Do not comment tests, private details, obvious locals, or routine helpers by default.
- Do not separately comment common interface implementations unless they add constraints, side effects, or behavior differences.
- Keep function-body comments rare and minimal.
- Write new or modified code comments in English unless the repository uses another language.
- Keep comments accurate, concise, and consistent with implementation.

## Cleanup Rules

- Replace stale, misleading, verbose, repetitive, or contradictory comments with accurate wording.
- Delete comments that repeat obvious code.
- Delete or consolidate docs that duplicate another source without audience-specific value.
- Prefer updating the canonical document over copying guidance.
- Keep good existing comments stable.
- For prose comments, treat wrapped lines as continuous text before judging width.
- Reflow prose comments so non-final lines stay near and under 80 columns; final lines may reach 90.

## Negative Constraints

- Do not treat documentation volume as quality.
- Do not use comments to compensate for unclear code when simplification is the real fix.
- Do not document speculation, unsupported workflows, or private details users should not depend on.
- Do not require comments for every private symbol, test helper, branch, or function body.
- Do not conflate docs issues with logic bugs, test gaps, or style-only preferences.

## Output Format

Start with prioritized findings. For each, include:

- Severity: `High`, `Medium`, or `Low`.
- Location: file and line number when available.
- Problem: missing, stale, noisy, misleading, or poorly scoped doc/comment.
- Impact: how it can confuse the audience.
- Improvement plan: the smallest practical wording, deletion, consolidation, or structure change.

After findings, include:

- Suggested outline or comment text only when useful and concise.
- Questions or assumptions, only if needed.
- Brief summary for non-trivial reviews.

If the docs and comments are already adequate for the observed scope, say that clearly and mention any residual risk from unavailable runtime, product, or audience context.
