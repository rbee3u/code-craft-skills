---
name: improve-documents
description: Assess or improve documentation and comments for accuracy, clarity, usefulness, scope, and implementation consistency. Use for README, AGENTS, docs, API docs, module docs, component docs, or code comments.
---

# Improve Documents

Docs and comments must earn their place: keep guidance accurate, actionable,
and scoped to its audience. Treat noise as a defect, not as thoroughness.

## Documentation Rules

- Verify content against actual code, config, and commands before judging it.
- Preserve good existing docs and comments; do not rewrite for stylistic
  uniformity.
- Update the canonical document instead of copying guidance into another file.
- Missing docs matter only when they block use, contribution, operation, or
  maintenance.

## Comment Rules

- Add or keep comments only when they explain what the code cannot: intent,
  constraints, caller obligations, workarounds, or surprising behavior.
- Comment public APIs when the language or project convention expects it; do
  not comment tests, private details, obvious locals, or routine helpers by
  default.
- Do not separately comment common interface implementations unless they add
  constraints, side effects, or behavior differences.
- Keep function-body comments rare and minimal; delete comments that restate
  the code.
- Write new or modified comments in English unless the repository uses another
  language.
- Reflow prose comments as continuous text: keep non-final lines near and under
  80 columns; final lines may reach 90.

## Negative Constraints

- Do not treat documentation volume as quality.
- Do not use comments to compensate for unclear code when simplification is the
  real fix.
- Do not conflate docs issues with logic bugs, test gaps, or style-only
  preferences.

## Output Format

List findings by priority, each with severity (`High`, `Medium`, `Low`),
location, problem, impact, and the smallest practical fix. If docs and comments
are already adequate, say so plainly.
