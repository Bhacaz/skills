# Multi-Lens Checklist

Use this checklist to ensure broad, relevant coverage without duplicating noise.

## 1) Correctness

- Are core invariants maintained?
- Do edge and failure paths behave safely?
- Are null/empty/timeout/retry cases handled?
- Is state transition logic sound?
- Are there any unhandled edge cases?
- When removing elements of any kind, are there still stale references anywhere in the project?

## 2) Architecture and Maintainability

- Does the change preserve clear boundaries?
- Is coupling introduced where it should not be?
- Is complexity increasing without payoff?
- Will this be easy to modify safely later?

## 3) Security

- Are all external inputs validated and constrained?
- Are authn/authz checks present at the right boundary?
- Any injection, traversal, SSRF, or data exposure risks?
- Are secrets/tokens/PII handled and logged safely?

## 4) Performance

- Any hot-path regressions?
- N+1 queries or repeated expensive operations?
- Unbounded loops, memory growth, or large payloads?
- Avoidable synchronous/blocking operations?

## 5) Testing and Regression Risk

- Are changed behaviors covered by tests?
- Are failure and edge conditions tested?
- Do tests assert outcomes, not implementation details?
- Is there obvious missing coverage for risky code?

## 6) API and Data Contracts

- Are external/internal contracts changed?
- Any breaking changes without migration strategy?
- Are defaults/backward compatibility preserved where required?
- Schema evolution safe for existing data?

## 7) Operability and DX

- Are error messages actionable?
- Is logging useful and not noisy or sensitive?
- Are metrics/tracing hooks needed for new critical paths?
- Is docs/runbook/config updated when behavior changes?
