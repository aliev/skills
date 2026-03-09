---
name: refactor
description: Improve code structure while preserving behavior. All tests must remain green.
---

# Refactor

## Goal
Improve code quality without changing observable behavior.

## Rules
- Do not change observable behavior.
- All tests must remain green.
- Do not remove or weaken existing tests.
- Prefer small, incremental changes.

## Allowed
- Remove duplication.
- Improve names.
- Extract functions or small modules.
- Simplify logic and control flow.
- Improve boundaries between components.

## Avoid
- Large rewrites.
- Adding layers without clear benefit.
- Introducing abstractions too early.
- Creating thin wrapper modules that hide no real complexity.

## Pragmatism
- If further refactoring would not meaningfully improve the code, say so.

## After refactoring
- Run the full test suite.
- Confirm all tests pass.
- Report what changed and why.
