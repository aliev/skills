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
