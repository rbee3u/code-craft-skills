---
name: improve-unit-tests
description: Assess or improve unit tests by finding key-path, scenario, boundary, failure, assertion, brittleness, maintainability, and regression-signal gaps. Use for unit test quality, not coverage percentage or implementation-detail coverage.
---

# Improve Unit Tests

Protect key paths with high-signal tests. Do not chase coverage percentage,
test count, or incidental implementation details.

## Priorities

- Assert externally observable behavior and stable contracts, not incidental
  steps or private details.
- Match coverage to risk; every reported gap must map to a concrete behavior
  risk, not a generic checklist.
- Organize by distinct scenarios; prefer parameterized or table-driven tests
  over near-duplicate cases.
- Simple behavior stays simply tested; do not add fixture systems, helper
  types, or mocks that outgrow the code under test.
- Clean up brittle, redundant, or unclear tests before adding more cases.
- If asked to edit, change tests only and run focused tests when practical.

## Negative Constraints

- Do not add near-duplicate tests with vague versioned names such as
  `TestSomethingV2`; extend one clear scenario or parameterized case instead.
- Do not force a single organization pattern; choose the simplest structure
  with strong signal.
- Do not test private details unless they expose real contract risk.

## Output Format

List findings by priority, each with severity (`Critical`, `High`, `Medium`,
`Low`), location, problem, impact, and the smallest practical change. If the
tests are already adequate for the observed risk, say so plainly.
