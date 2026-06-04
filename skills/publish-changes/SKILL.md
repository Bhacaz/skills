---
name: publish-changes
description: Prepare and publish local repository changes as a draft GitHub pull request using gh CLI, repository PR templates, git diff evidence, my-code-review, and manual testing notes.
---

# Publish Changes

Use this skill when the user asks to publish local changes, create a PR, open a draft PR, or prepare a PR description
from the current branch.

## Workflow

1. Confirm repository state:

- Run `git status --short`.
- Identify current branch with `git branch --show-current`.
- Identify base branch from existing upstream/PR metadata when available; otherwise use remote default branch from
  `git remote show origin` or `gh repo view --json defaultBranchRef`.
- Compute the review diff against `git merge-base HEAD <base>`.

2. Detect changes from Git:

- Use `git diff --stat <merge-base>...HEAD`.
- Use `git diff --name-status <merge-base>...HEAD`.
- Inspect relevant hunks with `git diff <merge-base>...HEAD -- <paths>`.
- If a branch name, commit, or diff mentions a Jira ticket, consider fetching the Jira issue for requirement context
  and manual testing clues.
- Treat Jira as context only. The git diff is the source of truth for what will be merged; Jira text may describe
  desired behavior, not the actual code change.
- Include staged and unstaged local changes when they are part of the intended PR. If intent is unclear, mention the
  ambiguity before publishing.

3. Review changes before publishing:

- Use the `my-code-review` skill against the detected diff.
- Fix actionable issues when the user asked for completion, or report blockers if a safe fix is not clear.
- Stop the publishing workflow when a blocking element is found. Ask the user what they want to do next before
  pushing, creating, or updating any PR.
- Do not create the PR while known high-severity review findings remain unresolved unless the user explicitly asks to
  publish anyway.

4. Find the repository PR template:

- Prefer `.github/pull_request_template.md`.
- If absent, check `.github/PULL_REQUEST_TEMPLATE/*.md`.
- If absent, check `PULL_REQUEST_TEMPLATE.md`.
- Preserve template headings, prompts, checkboxes, comments, and ordering unless the template clearly instructs
  removal.

5. Fill the PR template from the diff:

- Summarize what changed from `git diff`, not from guesswork.
- Explain why only when commits, branch name, ticket context, or changed code make it clear.
- Add risk/impact notes when the diff suggests them.
- For testing sections, do not cite unit test, lint, typecheck, or automation commands.
- Add manual testing steps to reproduce and verify the change.
- Use `N/A` for manual testing when the steps are not knowable from the diff or user context.

6. Choose the PR title:

- Start from the branch name.
- If the branch begins with a ticket key or number, keep that leading ticket first.
- Convert separators after the leading ticket into readable words.
- Examples:
  - `HPX/HUBQC-413-remove-bi-logger` -> `HPX/HUBQC-413 Remove BI logger`
  - `HUBQC-413-remove-bi-logger` -> `HUBQC-413 Remove BI logger`
  - `413-remove-bi-logger` -> `413 Remove BI logger`
  - `remove-bi-logger` -> `Remove BI logger`

7. Publish with `gh`:

- Push the branch if needed: `git push -u origin HEAD`.
- Create a draft PR with
  `gh pr create --draft --base <base> --head <branch> --title "<title>" --body-file <body-file>`.
- If a PR already exists for the branch, update it with `gh pr edit --title "<title>" --body-file <body-file>` instead
  of creating a duplicate. If the existing PR is not draft, do not claim it is draft; tell the user.
- Verify the stored PR body with `gh pr view --json title,body,isDraft,url`.

## Output

Final response must include:

- PR URL.
- Whether the PR is draft.
- Title used.
- Short summary of meaningful changes.
- Manual testing value written into the PR body.
- Any unresolved review findings or publishing blockers.
