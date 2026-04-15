---
name: session-debrief
description: End-of-session review. Logs what happened, updates project files in memory, and appends a summary to today's daily log.
triggers:
  - "debrief"
  - "wrap up"
  - "close session"
  - "log session"
---

# Session Debrief Skill

Captures what happened in the current working session, updates the memory system accordingly, and appends a log entry to the daily log file.

## When to Use

Run this skill at the end of a working session — before closing Claude Code.

Triggers: "debrief", "wrap up", "close session", "log session"

## Steps

1. **Ask the user three questions** (one at a time)

   Ask each question and wait for the answer before asking the next:

   - "What did you work on in this session?"
   - "What got completed or moved forward?"
   - "What is blocked, pending, or needs follow-up?"

2. **Identify which projects were touched**
   Based on the user's answers, identify which project files in memory need updating.
   Read the relevant project files from `~/.claude/projects/[workspace]/memory/`.

3. **Update project files**
   For each touched project:
   - Update `next_action` if it changed
   - Update `status` emoji if the project moved forward or stalled
   - Append a dated entry to the `## Status Log` section

4. **Update MEMORY.md index**
   Reflect any status changes in the one-line entries in `MEMORY.md`.

5. **Write today's daily log entry**
   Append a session summary to `daily-log/YYYY-MM-DD.md`.
   Create the file if it does not exist yet.

   Format:
   ```markdown
   ## Session — [HH:MM]

   **Worked on:** [summary of what was done]

   **Completed:** [what moved forward or closed]

   **Pending / Follow-up:**
   - [item 1]
   - [item 2]
   ```

6. **Confirm**
   Tell the user: which project files were updated, the path of the daily log entry written.

## Rules

- Always ask the three questions before writing anything.
- Do not invent or assume what was worked on — use only what the user says.
- If a project is mentioned that does not exist in memory, offer to create it.
- Keep log entries factual and brief — this is a record, not a narrative.
- Never delete or overwrite existing log entries — only append.
