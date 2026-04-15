---
name: daily-briefing
description: Generates a daily priority list by reading the memory index and recent session logs. Use at the start of a working day or session.
triggers:
  - "briefing"
  - "daily briefing"
  - "what's on today"
---

# Daily Briefing Skill

Reads the memory system and recent daily logs, then generates a structured priority list for the current day. Output is formatted as HTML and opened in the browser.

## When to Use

Run this skill at the start of a working day or session.

Triggers: "briefing", "daily briefing", "what's on today"

## Steps

1. **Read the memory index**
   Read `~/.claude/projects/[workspace]/memory/MEMORY.md`.
   Identify all active projects (🔴🟠🟡🟢) and their next actions.

2. **Read recent daily logs**
   Read the last 5 daily logs from `daily-log/` (most recent first).
   Look for:
   - Tasks marked as pending or incomplete
   - Notes or reminders carried forward
   - Context on what was happening recently

3. **Identify today's priorities**
   Build a priority list:
   - 🔴 Urgent items first (red status or time-sensitive)
   - 🟠 Stalled items that need a nudge
   - 🟡 Active work with a clear next action
   - Anything from recent logs that was not completed

4. **Generate the briefing**
   Produce a markdown document with these sections:

   ```markdown
   # Daily Briefing — [Day, Date]

   ## Today
   - [ ] [Highest priority task]
   - [ ] [Second priority]
   - [ ] [Third priority]

   ## Watch
   | Item | Status | Note |
   |------|--------|------|
   | [Stalled project] | 🟠 | [What you are waiting for] |

   ## Upcoming
   [Any deadlines or events in the next 7 days]

   ## Notes from Yesterday
   [Any incomplete items or reminders from the last session log]
   ```

5. **Render and open**
   Use the html-preview skill to render the briefing as HTML and open it in the browser.

## Rules

- Never modify memory files during this skill — read only.
- If the memory index does not exist, say so and suggest running setup.
- If there are no active projects, generate a minimal briefing and note that memory is empty.
- Keep the briefing concise — this is a scan, not a report.
