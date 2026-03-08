---
name: tdd
description: Strict TDD workflow with human checkpoints. One test at a time, minimal implementation, pause after green for human review.
---

# Strict TDD

## Loop

### 1. RED — One failing test
- Exactly one test for the next behavior.
- Public API only — no private attributes/methods.
- No production code yet.

### 2. Confirm RED
- Run tests, confirm the new test fails for the expected reason.

### 3. GREEN — Minimal implementation
- Smallest change that makes the test pass.

### 4. Confirm GREEN
- Run full test suite, all must pass.

### 5. CHECKPOINT — Return control to human

Report:
- What test was added.
- What made it GREEN.
- Test suite status.

Wait. The human may:
- Review changes.
- Request refactoring.
- Request a git commit.
- Instruct to continue.

Do NOT proceed to the next test until the human says so.
