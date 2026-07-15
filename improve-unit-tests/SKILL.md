---
name: improve-unit-tests
description: Improve unit tests by finding gaps in key-path coverage, scenario organization, boundaries, failure paths, assertions, brittleness, maintainability, and regression value, then producing prioritized improvement plans. Use when the user asks to assess or improve unit tests without optimizing for coverage percentage, test count, or implementation-detail coverage.
---

# Improve Unit Tests

Improve risk-based coverage, scenario clarity, behavior assertions, refactor-friendly structure, and maintainable test design. Protect key paths without chasing coverage percentage or freezing incidental implementation details.

## Workflow

1. Determine scope from the request, changed files, tests, production code, or local context.
2. Understand externally observable behavior before judging tests.
3. Map tests to key paths, distinct scenarios, boundaries, failures, and regression-prone cases.
4. Evaluate assertions, setup, helpers, naming, organization, determinism, and implementation coupling.
5. Decide whether to add tests, consolidate, rewrite brittle tests, or simplify structure.
6. Report only issues that materially affect confidence, maintainability, or regression protection.
7. Provide the smallest practical improvement plan. Do not edit tests unless asked.

## Improvement Priorities

- Assert externally observable behavior and stable contracts, not incidental steps.
- Match coverage to risk: key paths must be covered; percentage alone is not a goal.
- Cover boundaries, invalid inputs, failures, and fragile regressions when they carry real risk.
- Organize tests by distinct scenarios; avoid near-duplicate cases that differ only trivially.
- Use parameterized or table-driven tests when repeated patterns make cases clearer and less repetitive.
- Names, case grouping, assertions, setup, and helpers make intent obvious.
- Test data and fixtures stay minimal; remove repetition or noise that hides intent.
- Complex behavior may separate success and failure groups when it improves scanning.
- Simple behavior stays simply tested; avoid helpers, files, or fixtures that outgrow the code under test.
- Clean up brittle, redundant, or unclear tests before adding more cases.
- Tests stay deterministic and isolate order, time, randomness, I/O, shared state, and environment assumptions unless controlled.

## Negative Constraints

- Do not treat test count as a quality target.
- Do not chase coverage percentage at the expense of signal.
- Do not test private details unless they expose real contract risk.
- Do not add fixture systems, helper types, mocks, or files without clear value.
- Do not force one organization pattern; choose the simplest structure with strong signal.
- Do not add near-duplicate tests with vague versioned names such as `TestSomethingV2` when one clearer scenario or parameterized case would do.
- Do not report generic coverage gaps; tie each gap to concrete behavior risk.
- Do not ignore maintainability: noisy or brittle tests can reduce confidence.

## Output Format

Start with prioritized findings. For each, include:

- Severity: `Critical`, `High`, `Medium`, or `Low`.
- Location: test file and line number when available.
- Problem: coverage, assertion, brittleness, or maintainability issue.
- Impact: regression, false confidence, or maintenance cost.
- Improvement plan: the smallest practical test change, cleanup, or reorganization.

After findings, include:

- Missing behavior cases tied to concrete risk.
- Cleanup or consolidation opportunities that improve signal.
- Questions or assumptions, only if needed.
- Brief summary for non-trivial reviews.

If the tests are already adequate for the observed risk, say that clearly and mention any residual risk from limited scope or unavailable production context.
