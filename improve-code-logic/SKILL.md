---
name: improve-code-logic
description: Improve code logic by identifying behavioral correctness issues, edge cases, failure paths, state and data flow inconsistencies, and resource lifecycle risks, then producing prioritized fix plans. Use when the user asks to audit, inspect, review, or improve code logic without focusing on style-only feedback.
---

# Improve Code Logic

Improve code correctness, stability, predictability, and consistency with the intended semantics. Prioritize actual behavior risks over style, naming, formatting, or general maintainability advice.

## Workflow

1. Determine the improvement scope from the user request, staged diff, provided files, pull request, or relevant local code.
2. Read enough surrounding code to understand the contract, caller expectations, data model, state transitions, side effects, and error semantics.
3. Trace the normal path, boundary conditions, invalid inputs, empty or zero values, partial failures, retries, cancellation or interruption, and cleanup paths.
4. Compare each branch, return value, state mutation, emitted error, and external side effect against the intended behavior.
5. Report only issues with a plausible behavioral impact. Do not inflate style, structure, naming, comments, or test organization into logic findings unless they already cause incorrect behavior or a concrete implementation risk.
6. Separate confirmed findings from assumptions, open questions, and lower-confidence risks.
7. Provide a concrete fix plan for each real issue. Do not edit code unless the user explicitly asks for implementation.

## Improvement Priorities

- Correct branching, condition ordering, and fallback behavior.
- Consistent inputs, outputs, return values, errors, and state changes.
- Complete handling for null, empty, zero, invalid, malformed, duplicate, missing, out-of-range, and unexpected values.
- Correct behavior under partial success, failed dependencies, timeouts, cancellation, retries, and concurrent or repeated calls.
- Resource acquisition, release, reuse, ownership, and interruption paths that cannot leak, dangle, double-close, or reuse invalid state.
- Error semantics that expose the real failure and remain useful to callers or users.
- Data flow and state flow that preserve invariants across function, module, storage, network, and UI boundaries.
- Simpler implementations when they materially reduce behavior risk.

## Negative Constraints

- Do not report speculative issues that depend on unlikely assumptions without labeling them as assumptions.
- Do not treat every missing test as a logic bug. Mention missing tests only when they hide or fail to guard a concrete behavior risk.
- Do not focus on readability, architecture, or refactoring preferences unless they directly create a correctness risk.
- Do not recommend broad rewrites when a localized fix would address the behavior problem.
- Do not hide uncertainty. If the intended behavior is unclear, state the ambiguity and explain what evidence would resolve it.

## Output Format

Start with prioritized findings. For each finding, include:

- Severity: `Critical`, `High`, `Medium`, or `Low`.
- Location: file and line number when available.
- Problem: the incorrect or risky behavior.
- Impact: what can go wrong for callers, users, data, or runtime stability.
- Fix plan: the smallest practical correction.

After findings, include:

- Open questions or assumptions, only if needed.
- Test recommendations for the reported behavior risks, not generic coverage advice.
- A brief summary if the review is non-trivial.

If no logic issues are found, say that clearly and mention any residual risk from limited scope or missing runtime context.
