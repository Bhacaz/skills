# Review Workflow

## Phase 1: Scope and Intent

1. Identify the review target from user input:
   - staged changes
   - branch diff
   - commit or commit range
   - pull request
   - specific files
2. Extract stated requirements (if any).
3. If no requirements are provided, infer baseline expectations from existing
   code and conventions and note assumptions.

## Phase 2: Change Context Collection

1. Read the full diff and list touched files.
2. Classify changes and purpose for each file:
   - behavior change
   - refactor
   - data model/schema
   - API contract
   - auth/security
   - infrastructure/config
   - tests/docs only
3. Identify likely risk hotspots early.

## Phase 3: Multi-Lens Analysis

Evaluate the change set with each lens from `lenses.md`.

Guideline:
- Review beyond the diff when needed (callers, callees, tests, related config).
- Keep findings scoped to evidence and user goals.

## Phase 4: Confidence Pass

For each finding, assign confidence:
- High: directly evidenced by code path or contract.
- Medium: strongly likely but needs a small assumption.
- Low: hypothesis needing runtime/test confirmation.

Cull weak findings:
- Remove speculative claims without concrete support.

## Phase 5: Synthesis

Group findings into:
- Blockers
- Should Fix
- Suggestions

Then produce:
- verdict
- requirement coverage status (if requirements exist)
- clarifying questions that materially affect scope/correctness
- positive observations

Use `output-template.md` for response structure.
