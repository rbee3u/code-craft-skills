---
name: improve-code-logic
description: Improve code logic by finding correctness, simplicity, edge-case, failure-path, hot-path performance, flow, and resource lifecycle risks, then producing prioritized fix plans. Use when the user asks to assess or improve code behavior, not style-only concerns.
---

# Improve Code Logic

Improve correctness, stability, predictability, and semantic consistency. Favor simple, direct, elegant logic. Prioritize behavior and hot-path performance risks over style, naming, formatting, or general maintainability.

## Workflow

1. Determine scope from the request, diff, files, PR, or local code.
2. Read enough surrounding code to understand contracts, callers, data, state, side effects, resources, and errors.
3. Trace normal paths, boundaries, invalid inputs, partial failures, retries, cancellation, repeated calls, hot paths, and cleanup.
4. Compare branches, returns, mutations, errors, and external effects with intended behavior.
5. Report only plausible behavior risks; keep assumptions and uncertainty explicit.
6. Provide the smallest practical fix plan. Do not edit code unless asked.

## Improvement Priorities

- Branches, condition order, fallbacks, returns, and state changes match semantics.
- Null, empty, zero, invalid, malformed, duplicate, missing, out-of-range, and unexpected values are handled.
- Partial success, dependency failure, timeout, cancellation, retry, concurrency, and repeated-call behavior is correct.
- Hot paths avoid avoidable work, allocations, I/O, contention, or algorithmic cost.
- Resource ownership, release, reuse, and interruption paths cannot leak, dangle, double-close, or reuse invalid state.
- Errors expose the real failure and remain useful to callers or users.
- Data and state flow preserve invariants across boundaries.
- Simpler implementations reduce behavior risk; apply Occam's razor.

## Negative Constraints

- Do not present speculation as fact.
- Do not over-design or add defensive code for scenarios that cannot realistically occur.
- Do not turn style, structure, naming, comments, or test organization into logic findings unless they create behavior risk.
- Do not treat missing tests as logic bugs unless they hide or fail to guard a concrete risk.
- Do not report performance concerns outside hot paths unless they create a plausible user, cost, or stability risk.
- Do not recommend broad rewrites when a localized fix works.
- Do not hide unclear intent; state the ambiguity and needed evidence.

## Output Format

Start with prioritized findings. For each, include:

- Severity: `Critical`, `High`, `Medium`, or `Low`.
- Location: file and line number when available.
- Problem: incorrect or risky behavior.
- Impact: what can go wrong.
- Fix plan: the smallest practical correction.

After findings, include:

- Questions or assumptions, only if needed.
- Test recommendations tied to reported risks.
- Brief summary for non-trivial reviews.

If no logic issues are found, say that clearly and mention any residual risk from limited scope or missing runtime context.
