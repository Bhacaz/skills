# Severity and Verdict Rules

## Severity

- Critical
  - Security vulnerability with realistic exploit path
  - Data loss/corruption risk
  - Outage or severe correctness failure

- High
  - Major functional bug
  - Breaking contract without safe migration
  - Significant reliability/performance defect

- Medium
  - Maintainability or quality issue likely to cause near-term defects
  - Important test gaps in risky code

- Low
  - Minor clarity/style/refactor opportunities

- Info
  - Non-blocking observations and follow-ups

## Priority Buckets

- Blockers
  - Must be addressed before merge.
  - Usually Critical or High, but can include severe requirement gaps.

- Should Fix
  - Important non-blocking issues.
  - Worth fixing before merge or immediately after.

- Suggestions
  - Optional improvements with lower urgency.

## Verdict Logic

- REQUEST CHANGES
  - Any unresolved blocker exists.

- NEEDS DISCUSSION
  - Material requirement ambiguity remains.
  - Tradeoff requires product or architecture decision.

- APPROVE
  - No blockers.
  - Remaining items are non-blocking.

When in doubt, prefer explicit uncertainty over false confidence.
