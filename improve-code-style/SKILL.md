---
name: improve-code-style
description: Improve code style for naming, structure, cohesion, coupling, control flow clarity, abstraction quality, consistency, simplicity, and long-term maintainability. Use when the user asks to audit, inspect, review, or improve code style without focusing on pure logic bugs, missing tests, or comment coverage.
---

# Improve Code Style

Improve code style as a maintainability and clarity concern. Favor code that expresses intent directly, keeps responsibilities focused, and uses abstraction only when it reduces real complexity.

## Workflow

1. Determine the improvement scope from the user request, changed files, provided code, or relevant local context.
2. Read enough surrounding code to understand local conventions, module boundaries, naming patterns, and existing abstractions.
3. Evaluate names, structure, responsibility boundaries, control flow, consistency, abstraction choices, and complexity.
4. Prefer the project's existing conventions over generic preferences unless the convention itself creates clear maintenance cost.
5. Report only style issues that materially affect readability, consistency, cohesion, coupling, or maintainability.
6. Keep logic bugs, missing test coverage, and documentation gaps separate from style findings unless they are directly caused by style or structure choices.
7. Provide a concrete improvement plan. Do not edit code unless the user explicitly asks for implementation.

## Improvement Priorities

- Names should be accurate, natural, stable, and clear about responsibility, meaning, and boundaries.
- Functions, types, files, and modules should have focused responsibilities and avoid mixing unrelated concerns.
- Control flow should be direct and easy to follow; avoid unnecessary nesting, indirection, hidden conventions, and cleverness.
- Similar semantics should use consistent local patterns, including error handling, return paths, state changes, and helper usage.
- Moderate duplication is acceptable when removing it would introduce more indirection or weaker cohesion.
- Abstractions, interfaces, wrappers, layers, and extension points should have clear value beyond formal reuse.
- Simple problems should keep simple implementations; remove clever or generalized code that no longer earns its complexity.
- New packages, files, types, functions, or helpers should exist only when they clarify intent or reduce meaningful complexity.
- Similar modules should remain symmetrical in naming, structure, and local conventions even when they do not share common code.

## Negative Constraints

- Do not present personal taste as a style rule.
- Do not recommend abstraction for its own sake.
- Do not trade local readability, high cohesion, or low coupling for superficial reuse.
- Do not solve a simple issue with a more complex structure.
- Do not recommend new entities without a clear benefit over adjusting existing code.
- Do not weaken overall consistency through local naming, splitting, or structure choices.
- Do not treat formatter output or trivial whitespace as findings unless it conflicts with an enforced project standard.

## Output Format

Start with prioritized findings. For each finding, include:

- Severity: `High`, `Medium`, or `Low`.
- Location: file and line number when available.
- Problem: the naming, structure, complexity, consistency, or maintainability issue.
- Impact: why it makes the code harder to read, change, or reason about.
- Improvement plan: the smallest practical style or structure change.

After findings, include:

- Consistency notes, only when they help align related code.
- Open questions or assumptions, only if needed.
- A brief summary if the review is non-trivial.

If no meaningful style issues are found, say that clearly and mention any residual risk from limited scope or unknown project conventions.
