---
name: pr
description: Create a draft pull request using gh CLI.
---

# Pull Request

## Before creating
- Run linters and formatters configured in the project.
- Run unit tests. Do not run integration tests locally — delegate to CI.
- Review all commits on the current branch to build the summary.

## Creating
- Use `gh pr create --draft`.
- If the repo has a PR template, follow it.
- If no template, use this format:

## Why
<why this change exists, not what files changed>

## Changes
<brief list derived from branch commits>

<link related issues with Closes/Fixes #N>

## Rules
- Always draft. The human decides when to publish.
- Description focuses on why, not what.
- Link related issues when they exist.
- Push the branch before creating the PR.
