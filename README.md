# RPG Session Wiki

A static website publishing narrative recaps of *The Sleeper Beneath Mirrath* tabletop RPG campaign.
Raw session notes are transformed into dramatic, fantasy-novel-style prose and served as simple HTML pages.

## Prerequisites

You'll need [Claude Code](https://claude.ai/code) — Anthropic's AI coding assistant. The easiest
way to get started is the **Claude desktop app**: open it, go to the **Cowork** tab, and select
this project folder as your Cowork folder. Claude will have full access to the files and skills
in this repo. You can also run Claude Code in the terminal (`claude`) or via the VS Code extension
if you prefer.

After recording a new session, commit and push your changes to GitHub so the chronicle stays
backed up and your collaborators (or future you) can see the full history.

## Directory Structure

```text
wiki/
├── README.md              # This file
├── CLAUDE.md              # Always-on AI context: style rules, project conventions
├── .claude/
│   └── skills/
│       └── process-session/
│           └── SKILL.md  # The session-publishing pipeline (read this to understand the AI workflow)
├── style.css              # Shared stylesheet — edit here to change site appearance
├── templates/
│   ├── session.html       # Structural shell for new session pages
│   └── character.html     # Structural shell for new character journal pages
├── index.html             # Root index — links to all sessions with summaries
├── characters/            # One folder per player character
│   └── [name]/
│       ├── character.md   # Voice, backstory, equipment, and arc (source of truth)
│       └── index.html     # Character journal — first-person entries per session
└── session-N/             # One folder per play session (session-1, session-2, …)
    ├── notes.txt          # Raw session notes (source of truth)
    └── index.html         # Generated narrative for that session
```

## How the AI Workflow Works

This project uses a [Claude Code skill](.claude/skills/process-session/SKILL.md) — a reusable
instruction file that tells Claude exactly how to run the session-publishing pipeline. When you
trigger it, Claude reads the skill and follows its steps: auto-detecting the session number,
reading source files in parallel, generating prose, updating the index, writing character journal
entries, and updating each character's source file.

The skill lives at `.claude/skills/process-session/SKILL.md`. If you want to understand what
Claude does (or change how it behaves), that's the file to read and edit.

The companion file `CLAUDE.md` (at the project root) gives Claude always-on context: narrative
style rules, notes format, and where the character source-of-truth files live. Skills handle
*when and how* to run a workflow; `CLAUDE.md` handles *what this project is*.

## Adding a New Session

Open Claude Code in this folder. Then either:

**Option A — easiest:** Paste your raw session notes directly into the chat and say
**"process these session notes"**. Claude will automatically create the next `session-N/` folder,
save the notes, and run the full pipeline.

**Option B:** Create a `session-N/` folder manually, drop in a `notes.txt`, then say
**"session N is ready"** or type **`/process-session`**.

Either way, Claude runs the full pipeline automatically:

- `session-N/index.html` — narrative prose expanded from the notes
- Updated root `index.html` — new session card with summary and link
- Updated character journals — a new dated entry per character in `characters/[name]/index.html`
- Updated `character.md` files — new equipment, arc developments, relationship changes

## Changing the Site Theme

- **Colors, fonts, spacing only** — edit `style.css`. All pages update instantly; no regeneration needed.
- **Layout or structure changes** (e.g. adding a sidebar) — update the relevant template in `templates/`, then ask Claude to regenerate the affected pages using the new template.

## Campaign

**Title:** *The Sleeper Beneath Mirrath* (working title)

**Current status:** 3 sessions complete — party is Level 3.

### Player Characters

| Character         | Class / Race       | Notes                                          |
| :---------------- | :----------------- | :--------------------------------------------- |
| Mira Ashveil      | Rogue, half-elf    | Twin daggers; searching for her brother Corvan |
| Aldric Sorn       | Paladin, human     | Follower of Solrath (sun god); former soldier  |
| Vexa Crankwheel   | Artificer, gnome   | Carries a modified crossbow named Sprocket     |

### Key NPCs

| NPC             | Role                                                         |
| :-------------- | :----------------------------------------------------------- |
| Bess Collow     | Innkeeper, Dunholt; original party patron                    |
| Lena Croft      | Scholar from the Archive of Veth; temporary companion        |
| Vaeltharax      | Ancient red dragon entombed beneath the Mirrath mountains    |
| Captain Renfew  | Garrison commander of Dunholt; unmasked as the Hollow Priest |

## Narrative Style

- Third-person past tense, written like a chapter from a fantasy novel.
- Dramatic, atmospheric, and character-focused.
- Dice outcomes woven into the prose as moments of fate rather than mechanical results.
- DM notes used to inform tone and foreshadowing — never exposed directly.

## Notes Format

`notes.txt` files are extracted from handwritten PDF scans. They may include scene-by-scene
breakdowns, bullet-pointed events, dialogue snippets, dice results, NPC descriptions, and loot
or XP tracking.
