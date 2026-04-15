# Welcome to Big Brain

You just cloned this repo. Good. Here is what you have and what to do next.

---

## What is this?

Big Brain is a workspace template for people who want AI agents to actually understand their work — not just respond to one-off questions, but operate with full context about who you are, what your organization does, and what you are working on right now.

The idea: instead of explaining yourself every time you open a chat, you build a structured workspace that the agent reads automatically. Every conversation starts with context already loaded.

It is built for [Claude Code](https://claude.ai/code), Anthropic's AI coding and operations assistant.

---

## How it works — the short version

Three things make this system work:

**1. CLAUDE.md files — layered context**
Every folder has a `CLAUDE.md` that tells the agent what that area is about. The root one loads on every conversation. Subfolder ones load when you work in that area. You never have to re-explain your context.

**2. Memory system — continuity across sessions**
Projects, decisions, and lessons learned live in a `memory/` folder. The agent reads it at the start of each day and updates it at the end. Nothing gets lost between conversations.

**3. Domain subfolders — organized work**
Each area of your work (marketing, operations, clients, products) gets its own folder with its own context. The agent only reads what is relevant to the task at hand.

---

## Your first 20 minutes

Do these in order. Each step takes 3-5 minutes.

### Step 1 — Tell the agent who you are

Open `Person - Context.md` and fill it in. This is the most important file in the whole system. The agent will read this before doing anything for you.

Focus on:
- Your name and role
- What you actually do day-to-day
- How you like to work (tone, format, what to skip)

You do not need to be thorough right now. Even rough notes work. You will improve it over time.

### Step 2 — Tell the agent about your organization

Open `Organization - Context.md` and fill in the basics:
- What your company or project is called
- What you actually do and who you do it for
- Your team (even if it is just you)

Again, rough is fine. The goal is to give the agent something real to work with.

### Step 3 — Update CLAUDE.md

Open the root `CLAUDE.md`. Find the sections with `[PLACEHOLDER]` text and replace them:
- Workspace name (the `#` title at the top)
- Team section
- Structure section (add your real folders, remove the example ones)

Leave the rest as-is for now.

### Step 4 — Set up your first domain

The `my-domain/` folder is an example. Rename it to something real — the first area of your work you want to manage here.

```bash
mv my-domain marketing   # or: clients, operations, projects, content — whatever fits
```

Then open the `CLAUDE.md` and `Context.md` inside and fill in the basics for that area.

### Step 5 — Set up memory

Copy the memory templates to where Claude Code will auto-load them:

```bash
# Adjust the path: replace "Desktop/big-brain" with your actual workspace path
MEMORY_PATH="$HOME/.claude/projects/-Users-$(whoami)-Desktop-big-brain/memory"
mkdir -p "$MEMORY_PATH"
cp memory/*.md "$MEMORY_PATH/"
```

Open `MEMORY.md` in that folder and delete the example entries. Leave the headers.

### Step 6 — Run your first session

You are ready. Open this folder in Claude Code and type:

```
briefing
```

The agent will read your memory and generate your first priority list. It will be short — that is fine. Add your first real project to `memory/MEMORY.md` and it will grow from there.

---

## What to do when you are stuck

- **The agent does not seem to know your context** — check that `Person - Context.md` and `Organization - Context.md` are filled in, not still placeholders
- **Memory is not loading** — check the path in Step 5 matches your actual workspace location
- **You want to add a new area of work** — copy `my-domain/` and rename it, then fill in its `CLAUDE.md` and `Context.md`
- **You want to build a new skill** — copy one of the folders in `skills/`, rename it, and edit the `SKILL.md`

---

## When you are ready for more

Read [SETUP.md](SETUP.md) for a deeper walkthrough of each component.

Read the [README](README.md) for the full picture of how the system is designed.

Good luck.
