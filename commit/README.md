# /commit

Create a git commit using conventional commits format.

## What it does

Claude stages relevant files individually and creates a commit with a message that explains **why** the change was made, not what files were touched.

## Format

Uses [conventional commits](https://www.conventionalcommits.org/): `feat:`, `fix:`, `refactor:`, `test:`, `docs:`, `chore:`, etc.

## Safety

- Files are staged individually by name — never `git add .` or `git add -A`.
- One logical change per commit.
- Unrelated changes are not included.

## Pairs with

- `/tdd` — commit at CHECKPOINT after reviewing the RED-GREEN result.
- `/refactor` — commit refactoring separately from behavioral changes.
