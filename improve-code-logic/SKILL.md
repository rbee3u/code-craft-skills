---
name: improve-code-logic
description: Assess or improve code behavior by finding correctness, edge-case, failure-path, hot-path, flow, and lifecycle risks, then produce prioritized fix plans. Use for behavior, not style-only concerns.
---

# Improve Code Logic

Find and fix behavior risks. Prefer the smallest direct fix: simpler
implementations reduce behavior risk (Occam's razor).

## Priorities

- Rank findings by plausible real-world impact; keep evidence, inference, and
  uncertainty clearly separated.
- Flag performance only on hot paths where the cost is material.
- Prefer localized fixes over broad rewrites. If asked to edit, change only the
  targeted behavior and preserve unrelated code.

## Negative Constraints

- Do not add defensive code for scenarios that cannot realistically occur.
- Do not turn style, naming, comments, or missing tests into logic findings
  unless they create concrete behavior risk.
- Do not report performance concerns outside hot paths unless they create a
  plausible user, cost, or stability risk.

## Output Format

List findings by priority, each with severity (`Critical`, `High`, `Medium`,
`Low`), location, problem, impact, and the smallest practical fix plan. Add
test recommendations only when tied to reported risks. If no logic issues are
found, say so plainly instead of inventing findings.
