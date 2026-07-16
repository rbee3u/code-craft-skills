---
name: improve-code-logic
description: Assess or improve code behavior by finding correctness, edge-case, failure-path, hot-path, flow, and lifecycle risks, then produce prioritized fix plans. Use for behavior, not style-only concerns.
---

# Improve Code Logic

Improve correctness, stability, predictability, and semantic consistency. Tie
each recommendation to observable behavior or a defensible inference, and prefer
the smallest direct fix.

## Workflow

1. Determine scope from the request, diff, files, PR, or local code.
2. Read enough surrounding code to understand contracts, callers, data, state,
   side effects, resources, and errors.
3. Trace normal paths, boundaries, invalid inputs, partial failures, retries,
   cancellation, repeated calls, concurrency, hot paths, and cleanup.
4. Compare branches, returns, mutations, errors, and external effects with the
   intended behavior.
5. Rank only plausible behavior risks; separate evidence, inference, and
   uncertainty.
6. Provide the smallest practical fix plan. If asked to edit, make only targeted
   behavior changes and preserve unrelated code.

## Improvement Priorities

- Public contracts, caller expectations, and observable side effects stay
  consistent.
- Branches, condition order, fallbacks, returns, and state changes match
  semantics.
- Null, empty, zero, invalid, malformed, duplicate, missing, out-of-range, and
  unexpected values are handled where realistic.
- Partial success, dependency failure, timeout, cancellation, retry, concurrency,
  and repeated-call behavior is correct.
- Resource ownership, release, reuse, and interruption paths cannot leak,
  double-close, or reuse invalid state.
- Hot paths avoid avoidable work, allocations, I/O, contention, or algorithmic
  cost when the cost is material.
- Errors expose the real failure and remain useful to callers or users.
- Simpler implementations reduce behavior risk; apply Occam's razor.

## Negative Constraints

- Do not present speculation as fact.
- Do not over-design or add defensive code for scenarios that cannot
  realistically occur.
- Do not turn style, structure, naming, comments, or test organization into
  logic findings unless they create behavior risk.
- Do not treat missing tests as logic bugs unless they hide or fail to guard a
  concrete risk.
- Do not report performance concerns outside hot paths unless they create a
  plausible user, cost, or stability risk.
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
- Changed files and verification, only when edits were requested and made.
- Brief summary for non-trivial reviews.

If no logic issues are found, say that clearly and mention any residual risk
from limited scope or missing runtime context.
