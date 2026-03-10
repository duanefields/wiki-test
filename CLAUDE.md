# RPG Session Wiki

This project publishes narrative recaps of tabletop RPG sessions as a static website.

## Directory Structure

```text
wiki/
├── CLAUDE.md              # This file
├── .claude/
│   └── skills/
│       └── process-session/
│           └── SKILL.md  # Session-publishing pipeline
├── style.css              # Shared stylesheet — edit here to change site appearance
├── templates/
│   ├── session.html       # Structural shell for new session pages
│   └── character.html     # Structural shell for new character journal pages
├── index.html             # Root index — links to all sessions with summaries
├── characters/            # One folder per player character
│   ├── mira-ashveil/
│   │   ├── character.md   # Voice, backstory, equipment, arc — source of truth for generation
│   │   └── index.html     # Mira's journal — first-person entries per session
│   ├── aldric-sorn/
│   │   ├── character.md
│   │   └── index.html     # Aldric's journal
│   └── vexa-crankwheel/
│       ├── character.md
│       └── index.html     # Vexa's journal
└── session-N/             # One folder per play session (session-1, session-2, ...)
    ├── notes.txt          # Raw session notes (source of truth)
    └── index.html         # Generated narrative for that session
```

## Workflow

Session processing is handled by the `/process-session` skill. Once `notes.txt` is in place, say
"session N is ready" or `/process-session` — the skill runs the full pipeline automatically:
session narrative, root index update, all three character journal entries, and `character.md`
updates.

## Notes Format

`notes.txt` files are extracted from handwritten PDF notes. They are informal and may include:

- Scene-by-scene breakdowns
- Bullet-pointed events and dialogue snippets
- Dice roll outcomes
- NPC names and descriptions
- Loot/XP tracking
- DM notes (behind-the-scenes context — include in narrative only if appropriate as dramatic irony
  or foreshadowing)

## Narrative Style

- Write in third-person past tense, like a chapter from a fantasy novel
- Dramatic, atmospheric, and character-focused
- Preserve the actual character names and proper nouns exactly as written in the notes
- Dice outcomes can be woven in as moments of fate ("the gods favored her aim" rather than "she
  rolled a 19")
- DM notes are private context — use them to inform tone but do not expose them directly

## Character Journal Entries

Each character's `character.md` is the source of truth for their voice, header style, backstory,
equipment, and arc. Read it before generating any journal entry for that character.

- `characters/mira-ashveil/character.md`
- `characters/aldric-sorn/character.md`
- `characters/vexa-crankwheel/character.md`

After any session, update each `character.md` with new equipment, arc developments, and
relationship changes so it stays current.

## Current Campaign

**Campaign:** *The Sleeper Beneath Mirrath* (working title)

**Characters:**

- **Mira Ashveil** — half-elf rogue, twin daggers, searching for her lost brother Corvan
- **Aldric Sorn** — human paladin of Solrath (sun god), former soldier, deeply principled
- **Vexa Crankwheel** — gnome artificer, carries a modified crossbow named Sprocket

**Key NPCs:**

- Bess Collow — innkeeper, Dunholt; the party's original patron
- Lena Croft — scholar from the Archive of Veth; temporary companion
- Vaeltharax — ancient red dragon, entombed beneath the Mirrath mountains; antagonist/wildcard
- Captain Renfew — garrison commander of Dunholt; unmasked as the Hollow Priest

**Sessions so far:** 3 (party is Level 3 as of Session 3)
