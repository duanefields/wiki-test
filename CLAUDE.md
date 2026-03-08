# RPG Session Wiki

This project publishes narrative recaps of tabletop RPG sessions as a static website.

## Directory Structure

```
wiki/
├── CLAUDE.md              # This file
├── index.html             # Root index — links to all sessions with summaries
└── session-N/             # One folder per play session (session-1, session-2, ...)
    ├── notes.txt          # Raw session notes (source of truth)
    └── index.html         # Generated narrative for that session
```

## Workflow

When a new session folder is added or `notes.txt` is updated:

1. **Generate `session-N/index.html`** — Transform the raw notes into a dramatic fantasy-novel-style narrative. Expand bullet points and scene descriptions into prose. Preserve all key facts (names, places, outcomes, dice results if interesting). Do not invent events not implied by the notes.

2. **Update `root index.html`** — Add or refresh an entry for the session. Each entry should include:
   - Session number and title
   - Date played
   - A 2–3 sentence summary (written in the same narrative style)
   - A link to the session's `index.html`

## Notes Format

`notes.txt` files are extracted from handwritten PDF notes. They are informal and may include:
- Scene-by-scene breakdowns
- Bullet-pointed events and dialogue snippets
- Dice roll outcomes
- NPC names and descriptions
- Loot/XP tracking
- DM notes (behind-the-scenes context — include in narrative only if appropriate as dramatic irony or foreshadowing)

## Narrative Style

- Write in third-person past tense, like a chapter from a fantasy novel
- Dramatic, atmospheric, and character-focused
- Preserve the actual character names and proper nouns exactly as written in the notes
- Dice outcomes can be woven in as moments of fate ("the gods favored her aim" rather than "she rolled a 19")
- DM notes are private context — use them to inform tone but do not expose them directly

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
