---
name: my-code-review
description: High-signal, multi-perspective code review workflow for prioritized, actionable feedback
---

# Code Review Skill Pack

This skill pack defines a practical, high-signal code review process for the
`code-review` agent.

## Purpose

Provide consistent, high-quality review outcomes across:
- pull requests
- branch and commit diffs
- staged local changes
- targeted file/path reviews

## Core Principles

1. Evidence over opinion.
2. Risk over noise.
3. Actionable recommendations over abstract critique.
4. Preserve dissenting concerns when they are technically valid.
5. Clarify ambiguous requirements instead of guessing silently.
6. Orthographe, phrasing and typos

## Default Reviewer Lenses

- Correctness and logic safety
- Architecture and maintainability
- Security and trust boundaries
- Performance and scalability
- Testing and regression safety
- API and schema compatibility
- Operability and developer experience

See detailed checks in:
- `references/lenses.md`

## Severity and Verdict

Severity and merge recommendation rules are defined in:
- `references/severity-and-verdict.md`

## Workflow

Run the review using:
- `references/workflow.md`

## Final Output Contract

Use:
- `references/output-template.md`

## Constraint

This pack is standalone. It is tool agnostic and works with standard repository
exploration plus basic CLI tools.
