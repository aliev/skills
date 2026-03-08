# /pr

Create a draft pull request using `gh` CLI.

## What it does

Claude reviews all commits on the current branch, runs linters and unit tests, then creates a draft PR with a description focused on **why** the change exists.

## Before creating

- Runs linters and formatters configured in the project.
- Runs unit tests locally. Integration tests are left to CI.
- Reads all branch commits to build the summary.

## PR format

If the repo has a PR template, Claude follows it. Otherwise:

```markdown
## Why
<why this change exists>

## Changes
<brief list derived from branch commits>

Closes #123
```

## Rules

- Always creates a **draft** PR — the human publishes when ready.
- Links related issues when they exist.

## Pairs with

- `/tdd` — after multiple RED-GREEN cycles, create a PR for the feature.
- `/commit` — each checkpoint commit becomes part of the PR summary.
