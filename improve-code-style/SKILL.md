---
name: improve-code-style
description: Assess or improve code style by finding maintainability issues in naming, structure, cohesion, coupling, control flow, abstraction restraint, consistency, and simplicity. Use for style, not logic bugs, test gaps, or docs.
---

# Improve Code Style

Improve clarity and maintainability. Apply Occam's razor: favor direct code,
focused responsibilities, local consistency, and abstractions only when they
reduce real complexity.

## Workflow

1. Determine scope from the request, changed files, code, or local context.
2. Read enough surrounding code to learn conventions, boundaries, naming
   patterns, and abstractions.
3. Evaluate names, responsibilities, control flow, consistency, abstraction,
   coupling, cohesion, and complexity.
4. Prefer project conventions unless they create clear maintenance cost.
5. Report only issues with material readability, consistency, or maintenance
   impact.
6. Keep logic bugs, test gaps, and documentation gaps separate unless caused by
   style or structure.
7. Provide the smallest practical improvement plan. If asked to edit, avoid
   behavior changes and preserve unrelated code.

## Improvement Priorities

- Names are accurate, natural, stable, orderly, and clear about responsibility
  and boundaries.
- Functions, types, files, and modules stay focused and avoid mixed concerns.
- Control flow is direct and concise; avoid needless nesting, indirection,
  hidden conventions, and cleverness.
- Similar semantics use consistent local patterns for errors, returns, state
  changes, and helpers.
- Moderate duplication is acceptable when abstraction would add indirection or
  weaken cohesion.
- Abstractions, helpers, constants, wrappers, layers, and extension points have
  value beyond formal reuse.
- Simple problems stay simple; remove generalized code that no longer earns its
  cost.
- Keep logic local when extraction would mainly satisfy DRY rather than clarify
  intent.
- New packages, files, types, functions, helpers, or constants clarify intent or
  reduce meaningful complexity.
- Related files, functions, variables, and modules stay tidy and consistent
  without forcing a rigid pattern.

## Negative Constraints

- Do not present personal taste as a style rule.
- Do not recommend abstraction for its own sake.
- Do not extract helpers or constants merely to satisfy DRY.
- Do not trade readability, cohesion, or low coupling for superficial reuse.
- Do not solve a simple issue with a more complex structure.
- Do not add new entities without clear benefit over adjusting existing code.
- Do not weaken overall consistency through local naming, splitting, or
  structure.
- Do not treat formatter output or trivial whitespace as findings unless it
  conflicts with an enforced project standard.

## Output Format

Start with prioritized findings. For each, include:

- Severity: `High`, `Medium`, or `Low`.
- Location: file and line number when available.
- Problem: naming, structure, complexity, consistency, or maintainability issue.
- Impact: why the code is harder to read, change, or reason about.
- Improvement plan: the smallest practical style or structure change.

After findings, include:

- Consistency notes, only when they help align related code.
- Changed files and verification, only when edits were requested and made.
- Open questions or assumptions, only if needed.
- A brief summary if the review is non-trivial.

If no meaningful style issues are found, say that clearly and mention any
residual risk from limited scope or unknown project conventions.
