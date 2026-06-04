# Output Template

Use this format for all final reviews.

Add a number For each individual issue (eg: 1,2,3).
To easily reference the issue later in the chat session.

```markdown
# Code Review

## Verdict
- APPROVE | REQUEST CHANGES | NEEDS DISCUSSION
- One-sentence rationale.

## Blockers
- If none: "None."
- For each blocker include:
  - Severity
  - Location (`path/to/file.ext:line`)
  - Issue
  - Why it matters
  - Recommended fix

## Should Fix
- Important, non-blocking issues.
- Keep prioritized and concrete.

## Suggestions
- Optional improvements.
- Keep concise and practical.

## Requirements Assessment
- If requirements were provided:
  - Requirement -> Met | Partially Met | Not Met | Cannot Assess
- If no requirements were provided:
  - List assumptions used during review.

## Clarifying Questions
- Only questions that materially affect correctness, scope, or risk.

## What's Working Well
- 1-3 concrete strengths.
```

## Style Rules

- Prioritize correctness, safety, and compatibility before style.
- Use specific evidence with file references.
- Avoid broad statements without proof.
- Keep tone direct, respectful, and implementation-oriented.
