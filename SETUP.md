# Setup Guide (Optional)

This guide walks you through customizing Big Brain for your context.

You don't need to follow it — you can explore the files directly and adapt them however you want. This is here if you prefer a step-by-step walkthrough.

---

## Step 1 — Fork or clone

```bash
git clone https://github.com/marcogalluccio/big-brain.git my-workspace
cd my-workspace
```

Rename the folder to whatever makes sense for your workspace (e.g., `my-company`, `ops`, `brain`).

---

## Step 2 — Fill in Person - Context.md

Open `Person - Context.md` and fill in your profile. This file tells the agent who it is working with. The more specific you are, the better the agent's output will match your style.

Key things to fill in:
- Your name and current role
- Your background and areas of expertise
- How you like to communicate (tone, length, format)
- Your current goals and priorities

---

## Step 3 — Fill in Organization - Context.md

Open `Organization - Context.md` and describe your company or project. This is the background the agent needs to understand what you are building and why.

Key things to fill in:
- Company name, legal entity (if relevant), location
- Mission and what you actually do
- Your business lines or products
- Your team (even if it is just you)
- Key partners or stakeholders

---

## Step 4 — Edit CLAUDE.md

Open the root `CLAUDE.md`. Replace every `[PLACEHOLDER]` with your actual information:

- Workspace name and description
- Team members and their roles
- Folder structure (add or remove domains as needed)
- Rules specific to your context

The annotations in the file (HTML comments starting with `<!-- CUSTOMIZE:`) explain what each section is for.

---

## Step 5 — Set up your domains

The `my-domain/` folder is an example. For each area of your work, create a folder:

```bash
cp -r my-domain marketing
cp -r my-domain operations
cp -r my-domain clients
```

Then edit the `CLAUDE.md` and `Context.md` in each folder to describe that domain.

You can delete `my-domain/` once you have created your real folders.

---

## Step 6 — Set up the memory system

The `memory/` folder in this repo contains templates. In real use, memory lives at:

```
~/.claude/projects/[your-workspace-path]/memory/
```

Claude Code auto-loads `MEMORY.md` from this path when you open your workspace.

To set it up:

```bash
# Replace [your-workspace-path] with the actual path (dashes replace slashes)
# Example: ~/Desktop/my-workspace → -Users-yourname-Desktop-my-workspace
MEMORY_PATH="$HOME/.claude/projects/-Users-$(whoami)-Desktop-my-workspace/memory"
mkdir -p "$MEMORY_PATH"
cp memory/*.md "$MEMORY_PATH/"
```

Then open `MEMORY.md` in that folder and clear out the example entries — start fresh.

---

## Step 7 — Run your first daily briefing

Open your workspace in Claude Code and type:

```
briefing
```

The agent will read your `MEMORY.md` and any recent daily logs, then generate a priority list for today. On first run, it will be mostly empty — that is fine. Add your first project to `memory/MEMORY.md` and run it again.

---

## Step 8 — Run a session debrief

At the end of a working session, type:

```
debrief
```

The agent will ask what you worked on, what got done, and what is blocked. It will log the session to `daily-log/` and update your project files in memory.

---

## That's it

The system is running. From here:

- Add projects to `memory/MEMORY.md` as they come up
- Use `briefing` to start your day
- Use `debrief` to close a session
- Use `preview` to render any document in the browser
- Build new skills in `skills/` as you identify recurring tasks
