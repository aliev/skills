# Claude Code Skills

Custom skills for Claude Code that enforce a disciplined development workflow.

## Skills

| Skill | Command | Description |
|-------|---------|-------------|
| [TDD](/tdd) | `/tdd` | Strict RED-GREEN cycle with human checkpoints |
| [Refactor](/refactor) | `/refactor` | Improve code structure while tests stay green |
| [Commit](/commit) | `/commit` | Git commit with conventional commits format |
| [PR](/pr) | `/pr` | Draft pull request via `gh` CLI |

## Workflow

The skills are designed to work together:

```
/tdd
  RED   → write one failing test
  GREEN → minimal implementation
  CHECKPOINT → human decides:
    /refactor → clean up code
    /commit   → save progress
    continue  → next test
```

## Best practices

### At every CHECKPOINT

"Looks ok" is not a review. Ask yourself:

- Can I explain this change a week from now?
- Why this way and not another?
- Would I have written it differently? If so — why did the model decide otherwise?
- What happens if this gets nil? An empty list? Two identical values?

If you can't answer — don't approve. Ask the model "what alternatives did you consider?" or rewrite it yourself.

Don't memorize the solution — understand **why** it's shaped that way.

### The trade-off

Writing everything yourself is thorough but impractical. Approving everything blindly is fast but dangerous.

Balance:
- Design, decomposition, naming, choice of abstractions — yours.
- Boilerplate, migrations, edge case tests — model's.
- Sometimes write the test yourself, give the model only GREEN.
- Sometimes refactor yourself, ask the model just to run the tests.
- If you don't understand the model's solution — don't accept it.

The key is to never fully settle into one mode.

## Design principles

- **Minimal instructions.** Claude already knows TDD, refactoring, and git. Skills only add constraints that differ from default behavior.
- **Human in the loop.** Every behavioral change pauses for review. No runaway implementation.
- **Composable.** Each skill does one thing. Combine them at checkpoints.

## Inspiration

Articles:
- [Agentic Engineering Patterns](https://simonwillison.net/guides/agentic-engineering-patterns/) — Simon Willison
- [Martin Fowler on AI-assisted TDD](https://martinfowler.com/fragments/2026-02-18.html) — Martin Fowler

Similar skill (more verbose):
- [mattpocock/skills/tdd](https://github.com/mattpocock/skills/tree/main/tdd)

Books:
- *Clean Architecture* — Robert C. Martin
- *A Philosophy of Software Design* — John Ousterhout
