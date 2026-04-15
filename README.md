# Big Brain OS

An open-source operational workspace template powered by [Claude Code](https://claude.ai/code).

Big Brain OS gives you a structured system where AI agents understand your full context — who you are, what your organization does, and how your work is organized — before they do anything.

---

## The Three Core Ideas

### 1. CLAUDE.md Hierarchy

Every folder has a `CLAUDE.md` file that tells Claude Code what that area of the workspace is about. Files load top-down: the root `CLAUDE.md` sets global rules, subfolder `CLAUDE.md` files add domain-specific context.

```
CLAUDE.md                    ← global rules, team, structure, boot sequence
├── my-domain/
│   └── CLAUDE.md            ← domain-specific rules, what files to read
├── another-domain/
│   └── CLAUDE.md
└── skills/
    └── my-skill/
        └── SKILL.md         ← skill definition and instructions
```

The agent reads the root `CLAUDE.md` on every conversation. It reads subfolder `CLAUDE.md` files only when working in that area. This keeps context focused and avoids noise.

### 2. File-Based Memory System

Memory lives in `~/.claude/projects/[your-workspace]/memory/`. It persists across conversations and is the source of truth for what is active, what is planned, and what has been decided.

```
memory/
├── MEMORY.md                ← dashboard index — one line per item
├── project_*.md             ← one file per active project
├── strategic_*.md           ← long-term positioning and directions
├── feedback_*.md            ← lessons learned, agent behavior rules
└── reference_*.md           ← pointers to external resources
```

`MEMORY.md` is loaded automatically by Claude Code. Individual files hold full context and are read on demand. The **daily briefing** skill reads MEMORY.md to build your priorities each morning. The **session debrief** skill updates it at end of day.

### 3. Structured Domain Subfolders

Each area of your work gets its own folder with a `CLAUDE.md` and a `Context.md`. This lets you keep work organized without giving the agent everything at once.

```
my-domain/
├── CLAUDE.md        ← tells the agent what this domain is about
├── Context.md       ← background, goals, contacts, reference links
└── ...              ← your actual files (documents, spreadsheets, etc.)
```

---

## File Structure

```
big-brain-os/
├── README.md                    ← this file
├── SETUP.md                     ← optional guided setup walkthrough
├── CLAUDE.md                    ← root agent instructions (template)
├── Workflows.md                 ← cross-domain workflow patterns
├── .claudeignore                ← files excluded from Claude Code context
├── Person - Context.md          ← who you are: role, style, expertise
├── Organization - Context.md    ← your company/project: mission, team, products
├── my-domain/
│   ├── CLAUDE.md               ← domain instructions template
│   └── Context.md              ← domain context template
├── skills/
│   ├── daily-briefing/
│   │   └── SKILL.md            ← generates daily priority list from memory
│   ├── session-debrief/
│   │   └── SKILL.md            ← logs session and updates memory
│   └── html-preview/
│       └── SKILL.md            ← renders any markdown as styled HTML
├── daily-log/                   ← daily session logs (one file per day)
└── memory/                      ← memory system templates
    ├── MEMORY.md
    ├── project_template.md
    ├── strategic_template.md
    ├── feedback_template.md
    └── reference_template.md
```

---

## Quick Start

1. **Fork or clone** this repo into your working directory
2. **Fill in** `Person - Context.md` and `Organization - Context.md`
3. **Edit** `CLAUDE.md` — replace placeholders with your team and structure
4. **Rename** `my-domain/` to something real (e.g., `marketing/`, `operations/`)
5. **Copy** the `memory/` templates to `~/.claude/projects/[your-workspace]/memory/`
6. Open the folder in Claude Code — the agent will read your context automatically

See [SETUP.md](SETUP.md) for a step-by-step walkthrough.

---

## Skills Included

| Skill | What it does | Trigger |
|-------|-------------|---------|
| `daily-briefing` | Reads MEMORY.md + recent logs, generates a priority list for today | "briefing" |
| `session-debrief` | Logs what happened, updates project files in memory | "debrief" / "wrap up" |
| `html-preview` | Renders any markdown file as styled HTML and opens it in your browser | "preview" / "show me" |

Skills are defined in `SKILL.md` files. Each skill is self-contained and can be customized or replaced.

---

## Requirements

- [Claude Code](https://claude.ai/code) (CLI or desktop app)
- A folder you want to use as your operational workspace

No dependencies, no install scripts, no configuration files beyond what you edit manually.

---

## License

MIT — fork it, adapt it, build on it.
