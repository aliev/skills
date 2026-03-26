---
name: review-prep
description: Prepare the user to defend code changes on review. Walk through each change so the user understands the why, the alternatives, and can answer questions from colleagues.
---

# Review Prep — understand changes well enough to defend them

## What to do

Walk the user through recent code changes (in the current conversation or a specific PR) so they can confidently explain and defend every decision on review.

## How it works

1. **Go change by change.** Don't dump everything at once. One logical change at a time.

2. **For each change, cover:**
   - What it does (brief, one sentence)
   - Why this approach and not another (what alternatives exist, why they were rejected)
   - What could a reviewer question? Pre-answer the likely "why not X?" questions.

3. **Ask the user to explain it back.** After each change, ask them to restate in their own words. If they struggle, slow down and re-explain.

4. **Simulate reviewer questions.** Ask 1-2 questions a skeptical reviewer might ask. Let the user answer. Fill gaps if needed.

5. **Move on only when the user is confident.** Don't rush through changes to finish faster.

## Rules

- Read the actual code before explaining. Use real file paths and line numbers.
- Focus on decisions, not mechanics. The user doesn't need to know every line — they need to know why each decision was made.
- If a change was made to fix a bug, explain what caused the bug, not just the fix.
- Keep language simple. If the user can't explain it simply to a colleague, they don't understand it yet.
- If arguments are provided (e.g., `/review-prep #228`), focus on that PR. If not, use changes from the current conversation.

## Output

- Interactive conversation, not a monologue. Pause after each change for the user to engage.
- No files created unless the user asks for notes.
