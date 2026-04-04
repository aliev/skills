# Claude Code Skills

Custom skills for Claude Code that enforce a disciplined development workflow.

## Skills

| Skill                 | Command     | Description                                   |
| --------------------- | ----------- | --------------------------------------------- |
| [TDD](/tdd)           | `/tdd`      | Strict RED-GREEN cycle with human checkpoints |
| [Refactor](/refactor) | `/refactor` | Improve code structure while tests stay green |
| [Commit](/commit)     | `/commit`   | Git commit with conventional commits format   |
| [PR](/pr)             | `/pr`       | Draft pull request via `gh` CLI               |

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

Pause and review before approving. "Looks ok" is not a review. Ask yourself:

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
- Sometimes write the failing test yourself, then let the model implement just enough to pass it.
- Sometimes refactor yourself, ask the model just to run the tests.
- If you don't understand the model's solution — don't accept it.

The key is to never fully settle into one mode.

## Q&A

**Can I edit code myself at CHECKPOINT?**
Yes. Ask the model to commit, make your changes, then say "review" or "continue". The model will read the current state of the files.

**Can I commit first, then refactor?**
Yes, and it's safer. The commit locks the green state. If refactoring goes wrong, you can always roll back.

**Can I write the test myself?**
Yes. Write a failing test, then tell the model "I wrote a test, make it GREEN." See [example flow](/tdd/README.md#example-writing-the-test-yourself).

**When are abstractions introduced?**
At CHECKPOINT, through dialogue. GREEN produces naive code on purpose. You see the duplication and decide together with the model what to extract. Use `/refactor` for this.

**Do I need a separate skill for DDD, SOLID, etc.?**
No. At CHECKPOINT just say "extract this into a value object" or "this violates SRP, split it." The model understands these concepts without a dedicated skill. If you notice yourself repeating the same instructions — then make a skill.

**Will Claude forget the skill in a long session?**
The skill is injected once when you call `/tdd`. In long conversations context gets compressed. If the model drifts — call `/tdd` again to re-inject.

**If AI writes the code, does readability still matter?**
Yes. You review code at every CHECKPOINT — unreadable code is impossible to review properly. And the model reads your codebase too — the cleaner it is, the better it understands context and writes the next change.

**How do I avoid degrading as a developer?**
Alternate. Sometimes write the test yourself. Sometimes refactor yourself. The CHECKPOINT is not just for controlling the model — it's for keeping yourself in context. As long as you think at every pause, you don't degrade.

## Design principles

- **Minimal instructions.** Claude already knows TDD, refactoring, and git. Skills only add constraints that differ from default behavior.
- **Human in the loop.** Every behavioral change pauses for review. No runaway implementation.
- **Composable.** Each skill does one thing. Combine them at checkpoints.

## Inspiration

Articles:

- [Agentic Engineering Patterns](https://simonwillison.net/guides/agentic-engineering-patterns/) — Simon Willison
- [Martin Fowler on AI-assisted TDD](https://martinfowler.com/fragments/2026-02-18.html) — Martin Fowler
- [How AI Impacts Skill Formation](https://www.anthropic.com/research/AI-assistance-coding-skills) — Anthropic (2026)
- [mattpocock/skills/tdd](https://github.com/mattpocock/skills/tree/main/tdd) — similar skill (more verbose)

Books:

- _Clean Architecture_ — Robert C. Martin
- _A Philosophy of Software Design_ — John Ousterhout
