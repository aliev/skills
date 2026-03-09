# Best Practices: Working with AI through TDD

## Don't just approve — review

"Looks ok" is not a review. At every CHECKPOINT ask yourself: "Can I explain this change a week from now?" If not — you don't understand the code, you just approved it.

## How to understand code

Don't memorize the solution — understand **why** it's shaped that way. If you understand the reason, you can reconstruct the solution a week, a month, a year later.

Ask yourself: "why this way and not another?" If you can answer — you understand. If not — ask the model "what alternatives did you consider?" Comparing options builds understanding better than memorizing one.

Then try to break it mentally. "What happens if this gets nil? An empty list? Two identical values?" If you can predict the behavior — you understand it. If not — ask the model and verify the answer against the code.

## Stay a developer, not just an approver

The main risk of delegating to AI is that you stop thinking and just approve what it produces.

At every CHECKPOINT:
- Read the test. Do you understand what it checks and why?
- Read the implementation. Would you have written it the same way? If not — why did the model decide differently?
- Make design decisions yourself. The model proposes, you choose.

## Keep your skills sharp

- Sometimes write the test yourself, give the model only GREEN.
- Sometimes refactor yourself, ask the model just to run the tests.
- If you don't understand the model's solution — don't accept it. Ask "why?" or rewrite it yourself.

## When to write code yourself vs delegate

**Learning** — write yourself. Use the model for review and questions. Otherwise you learn to approve, not to write.

**Working** — delegate routine, keep the decisions. Design, decomposition, naming, choice of abstractions — yours. Boilerplate, migrations, edge case tests — model's.

**In practice** — alternate. The key is to never fully settle into one mode.

## Approving is a skill too

Good review is the ability to see what's wrong, ask the right question, suggest a better approach. The CHECKPOINT in `/tdd` trains this skill every iteration. But if you only approve and never write — you lose the intuition for why one solution is better than another. That intuition is built through writing, not reading.

Balance: write enough to keep your intuition alive, delegate enough to not waste time on routine.
