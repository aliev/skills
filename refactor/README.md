# /refactor

Improve code structure while keeping all tests green.

## When to use

At a `/tdd` CHECKPOINT when you see duplication, unclear names, or overly complex logic. Can also be used independently on any codebase with tests.

## What it does

Claude refactors code in small, incremental steps:
- Removes duplication
- Improves names
- Extracts functions or small modules
- Simplifies logic and control flow
- Improves boundaries between components

## What it won't do

- Change observable behavior
- Remove or weaken existing tests
- Large rewrites
- Add layers without clear benefit
- Introduce premature abstractions

## After refactoring

Claude runs the full test suite, confirms all tests pass, and reports what changed and why.

## Pairs with

- `/tdd` — call `/refactor` at CHECKPOINT when the naive GREEN code needs cleanup.
- `/commit` — commit the refactoring as a separate logical change.
