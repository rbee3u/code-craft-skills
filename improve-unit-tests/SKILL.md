---
name: improve-unit-tests
description: Improve unit tests for meaningful behavior coverage, boundary and failure-path coverage, assertion quality, brittleness, maintainability, and regression value. Use when the user asks to audit, inspect, review, improve, or plan unit tests without treating test count or implementation-detail coverage as the primary quality goal.
---

# Improve Unit Tests

Improve unit tests for risk-based coverage, clear behavior assertions, refactor-friendly structure, and maintainable test design. Treat tests as a tool for protecting intended behavior, not as a way to freeze incidental implementation details.

## Workflow

1. Determine the improvement scope from the user request, changed files, provided tests, related production code, or relevant local context.
2. Understand the externally observable behavior under test before judging the tests.
3. Map tests to key behavior paths, boundary conditions, failure branches, and regression-prone cases.
4. Evaluate assertion quality, data setup, helper usage, naming, organization, determinism, and coupling to implementation details.
5. Identify whether weak coverage should be fixed by adding tests, consolidating tests, rewriting brittle tests, or simplifying existing test structure.
6. Report only test issues that materially affect confidence, maintainability, or regression protection. Do not turn unrelated production-code style or logic concerns into unit-test findings.
7. Provide a concrete improvement plan. Do not edit tests unless the user explicitly asks for implementation.

## Improvement Priorities

- Assertions should target externally observable behavior and stable contracts rather than incidental internal steps.
- Coverage should match risk: critical paths, boundary cases, invalid inputs, failure modes, and historically fragile paths need stronger coverage.
- Test names, case grouping, assertions, setup, and helper APIs should make intent easy to understand.
- Test data and fixtures should stay minimal; remove repetition or noise that hides the behavior being checked.
- Parameterized or table-style tests should be used when they reduce duplication and clarify related cases, not as a mechanical template.
- Complex or important behavior may deserve separate groups for success paths and failure paths when that improves scanability.
- Simple behavior should remain simply tested; avoid splitting, helpers, files, or fixtures that make the tests more complex than the code under test.
- Existing brittle, redundant, or unclear tests should be cleaned up, merged, or rewritten before adding more cases on top.
- Tests should be deterministic and isolated from order, time, randomness, network, filesystem, shared state, and environment assumptions unless those dependencies are intentionally controlled.

## Negative Constraints

- Do not treat the number of tests as a quality target.
- Do not require tests for private implementation details unless those details expose real behavior risk through the public contract.
- Do not recommend broad fixture systems, helper types, mocks, or new test files without clear value.
- Do not over-prescribe one organization pattern; choose the simplest structure that preserves signal.
- Do not report missing coverage generically. Tie each gap to a specific behavior risk.
- Do not ignore test maintainability: noisy, brittle, or unreadable tests can reduce confidence even when they increase coverage.

## Output Format

Start with prioritized findings. For each finding, include:

- Severity: `Critical`, `High`, `Medium`, or `Low`.
- Location: test file and line number when available.
- Problem: the coverage, assertion, brittleness, or maintainability issue.
- Impact: what regression, false confidence, or maintenance cost it creates.
- Improvement plan: the smallest practical test change, cleanup, or reorganization.

After findings, include:

- Missing behavior cases, only when tied to concrete risk.
- Cleanup or consolidation opportunities, only when they improve test signal.
- Open questions or assumptions, only if needed.
- A brief summary if the review is non-trivial.

If the tests are already adequate for the observed risk, say that clearly and mention any residual risk from limited scope or unavailable production context.
