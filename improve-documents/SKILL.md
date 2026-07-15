---
name: improve-documents
description: Improve documentation and code comments for accuracy, clarity, usefulness, scope control, and consistency with implementation. Use when the user asks to audit, inspect, review, improve, or optimize README.md, AGENTS.md, docs files, API documentation, module, library, or component documentation, or code comments.
---

# Improve Documents

Improve documentation and comments as part of the engineering surface. Keep useful guidance accurate and easy to act on; remove or avoid comments and docs that only add noise.

## Workflow

1. Determine the improvement scope from the user request, changed files, docs directories, README, AGENTS files, API docs, or code comments.
2. Read enough related code, configuration, scripts, and tests to verify that the docs or comments match actual behavior.
3. Identify the intended audience: users, contributors, operators, API consumers, or coding agents.
4. Check whether each document or comment explains the right thing at the right level: purpose, constraints, usage, behavior, setup, commands, decisions, or non-obvious caveats.
5. Preserve good existing docs and comments. Do not rewrite merely for stylistic uniformity.
6. Report stale, misleading, redundant, missing, over-detailed, or poorly scoped documentation with concrete fixes.
7. Do not change unrelated logic, names, formatting, or tests under the cover of documentation cleanup unless the user explicitly asks.

## Documentation Priorities

- Documentation should match the current implementation, commands, configuration, file layout, public behavior, and supported workflows.
- README files should help a new reader understand what the project is, how to set it up, how to run or test it, and where to find deeper docs.
- AGENTS files should give coding agents concise, actionable project instructions: repository layout, build/test/lint commands, conventions, constraints, and workflow expectations.
- Docs under `docs/` or similar directories should have a clear audience, scope, and relationship to the source of truth.
- Usage examples, command snippets, environment variables, paths, and API references should be accurate and runnable where practical.
- Long docs should be structured for scanning with clear headings, stable terminology, and focused sections.
- Cross-references should point to useful canonical locations and should not create circular or stale guidance.
- Documentation should explain why, when, and how to use something, not restate code line by line.
- Missing documentation matters only when it blocks correct use, contribution, operation, review, or maintenance.

## Comment Priorities

- Add or keep comments only when they provide clear value.
- Public APIs and externally visible declarations should have concise comments when the language, framework, or project convention expects them.
- Comments should explain responsibility, constraints, preconditions, caller obligations, observable differences, compatibility reasons, protocols, workarounds, or surprising behavior.
- Test files, private implementation details, obvious local variables, and routine helper functions should not receive comments by default.
- Methods that implement common or external interfaces usually do not need separate comments unless the implementation adds constraints, side effects, or behavior differences.
- Function-body comments should be rare and minimal; keep them only for non-obvious protocols, compatibility reasons, workarounds, or easy-to-misread constraints.
- New or modified code comments should be written in English unless the repository explicitly uses another language for code comments.
- Comments must remain accurate, concise, and consistent with implementation.

## Cleanup Rules

- Replace stale, misleading, verbose, repetitive, or implementation-contradicting comments with more accurate wording.
- Delete comments that mechanically repeat obvious code behavior.
- Delete or consolidate documentation that duplicates another source without adding audience-specific value.
- Prefer updating the canonical document over copying the same guidance into many places.
- Keep qualified existing comments stable; do not rewrite them just to match a preferred phrase.
- When adding or modifying prose comments, treat existing wrapped lines as continuous text before judging width.
- Reflow prose comments so non-final lines stay close to 80 columns and do not exceed 80 columns; the final line may exceed 80 columns but should not exceed 90.

## Negative Constraints

- Do not treat documentation volume as a quality goal.
- Do not use comments to compensate for unclear code when a small code simplification is the real fix; report that separately.
- Do not document speculative behavior, unsupported workflows, or internal details that users should not depend on.
- Do not require comments for every private symbol, test helper, branch, or function body.
- Do not conflate documentation issues with pure logic bugs, test coverage gaps, or style-only preferences.

## Output Format

Start with prioritized findings. For each finding, include:

- Severity: `High`, `Medium`, or `Low`.
- Location: file and line number when available.
- Problem: the missing, stale, noisy, misleading, or poorly scoped documentation/comment issue.
- Impact: how it can confuse users, contributors, operators, API consumers, or coding agents.
- Improvement plan: the smallest practical wording, deletion, consolidation, or structure change.

After findings, include:

- Suggested doc outline or comment text only when it is useful and concise.
- Open questions or assumptions, only if needed.
- A brief summary if the review is non-trivial.

If the docs and comments are already adequate for the observed scope, say that clearly and mention any residual risk from unavailable runtime, product, or audience context.
