---
name: note
description: Save useful explanation or insight from the current conversation to ~/notes/claude-insights/ for future reference.
---

# Note — save insight to notes

## What to do

1. Look back through the current conversation and identify the most recent substantive explanation, insight, or solution that Claude provided. Focus on the last meaningful technical explanation, debugging insight, architectural decision, or problem-solving narrative.

2. Create a markdown file in `~/notes/claude-insights/` with the following naming convention:
   - Format: `YYYY-MM-DD-<short-slug>.md`
   - The slug should be 2-4 words describing the topic, kebab-case
   - Example: `2026-03-11-asyncio-memory-leak.md`

3. The file should contain:
   - A `# Title` summarizing the insight
   - `**Date:** YYYY-MM-DD`
   - `**Project:** <project name or path if available>`
   - `**Tags:** <relevant tags>`
   - Then the explanation itself, cleaned up for readability but preserving the original meaning and technical detail
   - If there was code involved, include relevant code snippets

4. After saving, print the file path so the user knows where to find it.

## Rules

- If the user provides arguments after `/note`, use them as a hint for what to save (e.g., `/note memory leak fix` — save the explanation about the memory leak fix).
- If no arguments and no clear recent explanation, ask the user what they want to save.
- Do NOT save trivial exchanges (greetings, confirmations). Only save substantive technical content.
- Keep the saved content concise but complete — it should be useful months later without additional context.
- If a file with the same slug already exists for today, append a number suffix (e.g., `-2`).
