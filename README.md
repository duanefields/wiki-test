# RPG Session Wiki

A static website publishing narrative recaps of *The Sleeper Beneath Mirrath* tabletop RPG campaign.
Raw session notes are transformed into dramatic, fantasy-novel-style prose and served as simple HTML pages.

## Directory Structure

```text
wiki/
├── README.md              # This file
├── CLAUDE.md              # AI workflow instructions
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

## Adding a New Session

1. Create a `session-N/` folder and drop in a `notes.txt` with the raw session notes.
2. Ask Claude to generate the session — it will produce all three of the following automatically:
   - `session-N/index.html` — narrative prose expanded from the notes
   - Updated root `index.html` — new session card with summary and link
   - Updated character journals — a new dated entry per character in `characters/[name]/index.html`
3. After generation, Claude will also update each `character.md` with new equipment, arc developments, and relationship changes.

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
