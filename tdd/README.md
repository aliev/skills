# /tdd

Strict TDD skill for Claude Code with human-in-the-loop checkpoints.

## How it works

The skill enforces a classic Red-Green-Refactor cycle, but replaces the automatic Refactor step with a **CHECKPOINT** where control returns to the human.

```
RED → GREEN → CHECKPOINT → (human decides) → RED → ...
```

### RED
Claude writes exactly one failing test. The test must use the public API only — no access to private attributes or methods. No production code is written at this step.

### GREEN
Claude writes the minimal implementation to make the test pass. No abstractions, no generalization — just enough to go green.

### CHECKPOINT
Claude reports what was done and **stops**. The human reviews and decides what happens next:

- **Refactor** — ask Claude to extract abstractions, rename, restructure. This is the natural moment for design decisions and code architecture discussions.
- **Commit** — ask Claude to commit. After the commit Claude keeps waiting — it does NOT start the next cycle.
- **Edit code yourself** — make manual changes, then ask Claude to review or continue.
- **Continue** — tell Claude to proceed with the next test. Only this moves to the next RED step.

## Why this flow works

- **Abstractions appear at the right time.** GREEN produces naive, duplicated code on purpose. Design decisions happen at CHECKPOINT through dialogue, not by accident.
- **Human stays in control.** Every behavior change goes through review before the next one starts. No runaway implementation.
- **Minimal skill, maximum effect.** The skill doesn't teach Claude what TDD is — it already knows. The skill only adds what's different: one test at a time, mandatory pause, explicit human approval to continue.

## Tips

- **Behavioral changes** — better to go through Claude so the TDD cycle stays coherent.
- **Cosmetic edits** — feel free to edit yourself, then tell Claude to continue.
- **Design discussions** — CHECKPOINT is the ideal moment. Ask Claude to propose patterns, extract classes, simplify. You approve or adjust.
- **Long sessions** — the skill is injected once when you call `/tdd`. If Claude drifts in a long conversation, call `/tdd` again to re-inject the instructions.

## Example: writing the test yourself

1. You call `/tdd` and describe the task
2. Model writes the first test → GREEN → CHECKPOINT
3. You say "/commit, continue"
4. Model writes the second test → GREEN → CHECKPOINT
5. You decide to write the next test yourself — open the file, write a failing test
6. Tell the model: "I wrote a test, make it GREEN"
7. Model reads your test, implements minimal code, runs tests → CHECKPOINT
8. You review the implementation — do you understand why it's shaped that way?

## Pairs with

- `/refactor` — call at CHECKPOINT to improve code structure while tests are green.
- `/commit` — call at CHECKPOINT to commit the current RED-GREEN result.
