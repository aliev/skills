# Best Practices

## At every CHECKPOINT

"Looks ok" is not a review. Ask yourself:

- Can I explain this change a week from now?
- Why this way and not another?
- Would I have written it differently? If so — why did the model decide otherwise?
- What happens if this gets nil? An empty list? Two identical values?

If you can't answer — don't approve. Ask the model "what alternatives did you consider?" or rewrite it yourself.

Don't memorize the solution — understand **why** it's shaped that way.

## The trade-off

Writing everything yourself is thorough but impractical. Approving everything blindly is fast but dangerous.

Balance:
- Design, decomposition, naming, choice of abstractions — yours.
- Boilerplate, migrations, edge case tests — model's.
- Sometimes write the test yourself, give the model only GREEN.
- Sometimes refactor yourself, ask the model just to run the tests.
- If you don't understand the model's solution — don't accept it.

The key is to never fully settle into one mode.
