# [YOUR WORKSPACE NAME]

<!-- CUSTOMIZE: Replace the title above with your workspace name.
     Write 2-3 sentences describing what this workspace is for.
     Example: "Central operational workspace for Acme Inc. — a product studio based in Berlin.
     Covers product development, client work, marketing, and internal operations." -->

[Short description of what this workspace is and what it covers.]

For full context on who is behind this workspace, see:
- `Person - Context.md` — who you are, your role, your working style
- `Organization - Context.md` — company overview, mission, team, products

## Team

<!-- CUSTOMIZE: List the people who use this workspace. Include their role and what areas
     they own. This helps the agent understand who is responsible for what.
     Remove this section if you work alone — or keep it with just yourself. -->

**[Your Name]** — [Role]
[One sentence on what they lead or focus on.]

**[Collaborator Name]** — [Role]
[One sentence on what they handle.]

## Agent Boot Sequence

<!-- This section tells Claude Code what to load at the start of every conversation.
     The files listed here are auto-loaded. You can add to this list if needed,
     but keep it short — only files the agent needs on every task. -->

These files are auto-loaded by Claude Code (no action needed):
- This file (CLAUDE.md)
- Memory index (MEMORY.md in ~/.claude/projects/[your-workspace]/memory/)

On every new conversation, before doing anything else:
1. Read today's daily log: `daily-log/YYYY-MM-DD.md` (if it exists)
2. Read the subfolder CLAUDE.md for whatever area the task touches

Load on demand (only when the task requires it):
- `Person - Context.md` — for tasks related to personal voice, style, or positioning
- `Organization - Context.md` — for formal documents, outreach, positioning
- `Workflows.md` — for cross-cutting processes and pipelines
- Subfolder context files — when working deep in a specific domain

## Structure

<!-- CUSTOMIZE: List your actual folders here. Add a one-line description for each.
     Remove or rename as needed. -->

- `Person - Context.md` — personal profile: role, style, expertise, goals
- `Organization - Context.md` — company overview: mission, team, products, partners
- `Workflows.md` — cross-domain processes and pipelines
- `my-domain/` — [replace with your actual domain name and description]
- `daily-log/` — session notes and daily logs. One file per day.
- `skills/` — automation skills (briefing, debrief, html-preview, and any you add)

## Memory System

<!-- The memory system is how the agent tracks active projects, strategic decisions,
     and lessons learned across conversations. It lives outside the workspace folder
     so it persists even if you move or rename the workspace.
     Path: ~/.claude/projects/[your-workspace-path]/memory/ -->

Memory lives in `~/.claude/projects/[your-workspace]/memory/` (auto-loaded by Claude Code).

Three categories:
- **Projects** — active work with status, next action, and deadline. Updated by debrief.
- **Strategic** — long-term directions and positioning. Updated when strategy shifts.
- **Feedback** — lessons learned and agent behavior rules. Updated when you correct the agent.

`MEMORY.md` is the index. Individual files hold full context. The daily briefing reads
MEMORY.md to build priorities. The session debrief updates project files when status changes.

Project status codes:
- 🔴 urgent / needs attention now
- 🟠 stalled / waiting on someone
- 🟡 active / in progress
- 🟢 confirmed / on track
- 🔵 done but loose ends open
- ❌ closed or cancelled

## Rules

<!-- CUSTOMIZE: Add your own rules here. These are enforced on every task.
     The rules below are sensible defaults — keep what applies, remove what doesn't. -->

- Never push to GitHub or deploy anything without explicit confirmation.
- Never modify legal documents, contracts, or sensitive files without permission.
- Never commit API keys, credentials, or personal data.
- When making structural changes (CLAUDE.md files, memory, skill definitions),
  propose the change and get confirmation before writing.
- When brainstorming copy or content variations, present multiple options in chat.
  Apply the chosen one only after confirmation.
- Language: keep all internal files in English unless otherwise specified.

## Keywords

<!-- CUSTOMIZE: Define shorthand commands the agent should recognize.
     These are natural language triggers that map to specific actions. -->

- **"briefing"** — run the daily-briefing skill
- **"debrief" / "wrap up"** — run the session-debrief skill
- **"preview" / "show me"** — render the current document as HTML in the browser
