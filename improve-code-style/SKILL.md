---
name: improve-code-style
description: Assess or improve code style by finding maintainability issues in naming, structure, cohesion, coupling, control flow, abstraction restraint, consistency, and simplicity. Use for style, not logic bugs, test gaps, or docs.
---

# Improve Code Style

Improve clarity and maintainability. Apply Occam's razor: favor direct code,
focused responsibilities, and local consistency; add abstractions only when
they reduce real complexity.

## Priorities

- Follow existing project conventions unless they create clear maintenance
  cost; consistency beats personal taste.
- Similar semantics use consistent local patterns for errors, returns, state
  changes, and helpers; keep related files, functions, and modules aligned
  without forcing a rigid pattern.
- Moderate duplication is acceptable when abstraction would add indirection or
  weaken cohesion; do not extract helpers or constants merely to satisfy DRY.
- New packages, files, types, functions, or constants must clarify intent or
  reduce real complexity, not just add structure.
- Simple problems stay simple; remove generalized code that no longer earns its
  cost.
- Report only issues with material readability, consistency, or maintenance
  impact. If asked to edit, avoid behavior changes and preserve unrelated code.

## Negative Constraints

- Do not recommend abstractions, layers, or extension points for their own sake
  or for hypothetical future needs.
- Do not weaken overall consistency through local renaming, splitting, or
  restructuring.
- Do not treat formatter output or trivial whitespace as findings unless an
  enforced project standard is violated.

## Output Format

List findings by priority, each with severity (`High`, `Medium`, `Low`),
location, problem, impact, and the smallest practical change. If no meaningful
style issues are found, say so plainly.
