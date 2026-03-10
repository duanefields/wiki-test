---
name: process-session
description: >
  Processes a new RPG session from raw notes all the way to published HTML. Use this skill
  whenever the user says "process session notes", "I took session notes", "new session is ready",
  "generate the session page", "session 4 notes are in", or "/process-session". Also trigger when
  the user drops raw session notes in the chat or says they just got home from a game. Runs the
  full pipeline: session narrative → root index update → three character journal entries → three
  character.md updates.
---

# Process Session

You are orchestrating a full session-publishing pipeline for *The Sleeper Beneath Mirrath* campaign wiki. This is a 6-step workflow that transforms raw notes into a published HTML narrative and three first-person character journal entries.

Use `TodoWrite` to track your progress. Mark each step complete as you finish it — the user can see your progress and it helps you stay oriented in a long task.

---

## Step 0 — Identify the session and locate the notes

**If the user pasted or attached raw notes directly in the chat:**
- Glob `session-*/` to find the highest existing session number, then increment by 1
- Create the new `session-N/` directory
- Write the pasted content to `session-N/notes.txt`
- Proceed with that session number

**If the user named a session number (e.g. "session 4"):** use that folder.

**Otherwise:**
- Glob `session-*/` directories
- Find the folder that has a `notes.txt` but no `index.html`, or whose `index.html` is older than `notes.txt`
- If still ambiguous, ask the user

---

## Step 1 — Read all source material in parallel

Fire these reads simultaneously:

- `session-N/notes.txt` — the raw source of truth
- `characters/mira-ashveil/character.md`
- `characters/aldric-sorn/character.md`
- `characters/vexa-crankwheel/character.md`
- `templates/session.html` — for the HTML structure
- An existing session page (e.g. `session-3/index.html`) — to match the writing style

Do not start writing until all reads are complete.

---

## Step 2 — Generate `session-N/index.html`

Use `templates/session.html` as your structural shell. Fill in:

- **Title** — invent a short, evocative title (2–5 words) that captures the session's dramatic core
- **Session meta** — session number in the `<p class="session-meta">` line
- **Date played** — use the date from `notes.txt` if present, otherwise ask the user
- **Narrative prose** — see style rules below
- **Earned This Session** — loot, XP, key items gained
- **Questions Left Unanswered** — hooks, cliffhangers, unresolved threads
- **Pagination links** — update the prev session link; omit next (it doesn't exist yet)
- **Nav session links** — add the new session's roman-numeral link to the `<nav>` block

### Narrative style rules

These are non-negotiable. Read the notes once to understand what happened, then write as if you are a novelist:

- **Third-person past tense.** "Mira stepped into the shadow." Not "Mira steps."
- **Atmospheric and character-focused.** Open with scene-setting. Let the characters' personalities drive the prose.
- **No invented events.** You may expand, dramatize, and add texture — but every plot beat must trace back to something in the notes.
- **DM notes are backstage context.** Use them to inform tone, dramatic irony, and foreshadowing, but do not state them directly. If the DM noted that an NPC is secretly a traitor, you can write the NPC as subtly unsettling — not explicitly villainous.
- **Dice outcomes as fate.** A natural 20 is "the gods favored her aim." A critical failure is "the fates were unkind." Weave these in; don't just say "she rolled well."
- **Scene headings with `<h2>`.** Divide the narrative into 3–5 scenes.
- **Dialogue with `<blockquote>`.** Use sparingly — only for lines actually in the notes or clearly implied.

---

## Step 3 — Update root `index.html`

Add a new `<a class="session-card">` block inside `.sessions-section`, following the exact pattern of existing cards:

```html
<a href="session-N/index.html" class="session-card">
  <div class="card-header">
    <span class="card-number">Session [Roman numeral]</span>
    <span class="card-date">[Month Day, Year]</span>
  </div>
  <div class="card-title-row">
    <span class="card-title">[Title]</span>
    <span class="card-arrow">&#8594;</span>
  </div>
  <p class="card-summary">[2–3 sentence summary in narrative style]</p>
</a>
```

The summary should read like back-cover copy — present the dramatic stakes, not a plot synopsis.

---

## Step 4 — Append journal entries to character pages

Each character has a journal at `characters/[name]/index.html`. Add a new `<article>` entry at the **top** of the journal entries (most recent first), inside whatever container holds the entries. Match the existing entry markup exactly.

Write **4–6 paragraphs** per character, first-person past tense. Each character's `character.md` (already read in Step 1) is the source of truth for their voice, header style, focus, and current arc — use it. Each character experienced the same session differently; emphasize what matters *to them* based on who they are.

**DM notes stay backstage here too.** Characters only know what their character would know.

---

## Step 5 — Update all three `character.md` files

After the session, each character's `character.md` needs to reflect the new state of the world. Update:

- **Equipment** — add new items, remove consumed ones
- **Relationships** — note any shifts
- **Personal Arc** — advance or add to the arc status
- **Session Arc Notes** — append a bullet for the new session: `- **Session N:** [1–2 sentence summary of their arc beat]`
- **Level** — if they leveled up, update it

Keep each `character.md` as the canonical source of truth for future generation.

---

## Step 6 — Final check

Before reporting done, verify:

- [ ] `session-N/index.html` exists and has real prose (not placeholder text)
- [ ] Root `index.html` has the new session card
- [ ] All three character journals have a new entry at the top
- [ ] All three `character.md` files are updated
- [ ] No placeholder text like `[Session Title]` or `[Loot or XP item]` remains in any file
- [ ] CSS paths are correct: session pages use `../style.css`, root uses `style.css`

Report a brief summary of what was generated: session title, number of words in the narrative, and one sentence about each character's journal entry.
