# Workflows

Cross-domain processes that span multiple folders or involve multiple steps.

<!-- CUSTOMIZE: This file documents recurring multi-step workflows.
     When a task involves more than one folder or more than one tool, it belongs here.
     Add your own workflows below — remove the examples that don't apply to you. -->

Read this file when:
- Working on a task that touches multiple domains
- Running a recurring process end-to-end
- Onboarding a new collaborator

---

## Workflow Template

Use this structure for each workflow:

**Trigger:** What starts this workflow (an event, a command, a recurring schedule)
**Steps:**
1. Step one
2. Step two
3. Step three
**Output:** What the workflow produces
**Files involved:** Which folders/files are touched

---

## Example Workflow 1: Content Pipeline

**Trigger:** A new content idea is ready to develop

**Steps:**
1. Add the idea to `my-domain/ideas.md` (or equivalent)
2. Develop the content (outline, draft, review)
3. Produce the final format (post, video script, article)
4. Publish to the relevant channel
5. Log the result in the session debrief

**Output:** Published content piece
**Files involved:** `my-domain/`, `daily-log/`, `memory/`

---

## Example Workflow 2: Project Lifecycle

**Trigger:** A new project is confirmed or starts

**Steps:**
1. Create a project file in `~/.claude/projects/[workspace]/memory/project_[name].md`
2. Add an entry to `MEMORY.md` with 🟡 status
3. Create a subfolder if the project needs dedicated files
4. Work on the project across sessions, updating the project file via debrief
5. When complete, update status to ❌ and archive the project file

**Output:** Tracked project with full history
**Files involved:** `memory/`, relevant domain folder

---

## Example Workflow 3: Contact / Lead Pipeline

**Trigger:** A new contact or potential client is identified

**Steps:**
1. Add the contact to your CRM or contact list (in the relevant domain folder)
2. Log the first interaction in the project or contact file
3. Follow up at the cadence defined in the project file
4. When a conversation moves forward, create a dedicated project file in memory
5. Track status through 🟠 (waiting) → 🟡 (active) → 🟢 (confirmed)

**Output:** Tracked relationship with clear next actions
**Files involved:** relevant domain folder, `memory/`
