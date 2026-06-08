Use model claude-sonnet-4-6.

# /upgrade — Upgrade free template to full system

You are upgrading this second brain from the free template to the full system.

## RULES
- NEVER overwrite existing files — only CREATE missing ones
- NEVER touch notes in 00-inbox/, 01-sources/, 02-knowledge/, 03-content/, 04-decisions/, 05-projects/
- NEVER overwrite the user's CLAUDE.md — only ADD missing sections at the end
- Report every action taken

---

## Step 1 — Check what already exists

Check for the existence of these files and note which are missing:
- .claude/commands/ingest.md
- .claude/commands/weekly.md
- .claude/commands/create-content.md
- .claude/commands/query.md
- .claude/commands/compact-sessions.md
- templates/knowledge.md
- templates/decision.md
- templates/project.md
- 06-system/context-live.md

Display a checklist to the user showing what exists (✅) and what will be created (➕).
Ask: "Ready to upgrade? (yes / no)"
Wait for confirmation before continuing.

---

## Step 2 — Create missing command files

Create .claude/commands/ folder if it doesn't exist.

For each missing command file, create it with the exact content below.

### .claude/commands/ingest.md
```
Use model claude-haiku-4-5.

# /ingest — Process raw sources

## SETUP — Read first
Before doing anything, read CLAUDE.md and extract:
- {{LANG}} — the vault's configured language (Language field)
- {{PILLARS}} or {{PROJECTS}} — the user's content pillars or active projects
- {{PROFILE}} — the user's profile if present (content creator / builder / researcher / entrepreneur / personal)

All output to the user must be in {{LANG}}.

---

## CRITICAL RULE
Maximum 3 files per session. If 00-inbox/ has more than 3 files, list them all and ask the user which ones to process first.

---

## Step 1 — Inventory
List files in 00-inbox/ (listing only — do not read yet).
If more than 3 files: display the list and ask which to prioritize.
If 3 or fewer: confirm and proceed.

## Step 2 — Process (one file at a time)

For each selected file:

1. Read the raw file
2. Create a structured note in 01-sources/ using this structure:

---
date: [today's date]
source: [name or author]
url: [if available]
tags: [relevant keywords]
---

[Title — descriptive]

## Summary
- [point 1]
- [point 2]
- [point 3]

## Key quote
> [exact quote if available, otherwise omit]

## What I retain
[Personal insight — connect to pillars or projects specifically]

## Links
- [[related note if relevant]]

3. File naming: [domain]-[date]-[short-slug].md
4. Delete the raw file from 00-inbox/ after successful creation

## Step 3 — Update context-live.md
After all files are processed, if 06-system/context-live.md exists:
- Update the inbox count (count remaining files in 00-inbox/)

## Step 4 — Summary
Display:
- How many files processed
- Names of notes created in 01-sources/
- How many files remain in 00-inbox/
- Suggestion: run /query or /create-content next
```

### .claude/commands/query.md
```
Use model claude-haiku-4-5.

# /query — Search the vault

## SETUP — Read first
Before doing anything, read CLAUDE.md and extract:
- {{LANG}} — the vault's configured language
- {{PROFILE}} — user profile (content creator / builder / researcher / entrepreneur / personal)

All output to the user must be in {{LANG}}.

---

## Step 1 — Identify the question
If the user typed a question after /query → use it directly.
If they typed /query alone → ask them what they want to know.

## Step 2 — Search the vault

Use Grep to find relevant keywords, then Read only the matching files.
Never read entire folders — search first, read second.

Search order:
- Content creator: 01-sources/ → 02-knowledge/ → 03-content/stock/
- Builder: 05-projects/ → 01-sources/ → 04-decisions/
- Researcher: 02-knowledge/ → 01-sources/
- Default: 01-sources/ → 02-knowledge/

## Step 3 — Respond

Structure:
[The question, restated]
[Synthesized answer based only on vault notes]

Sources used:
- [[note-1]] — [what this note contributes]

Gaps:
[What is missing in the vault on this topic]

## ABSOLUTE RULE
If no note covers the topic → say so clearly.
Never answer from general knowledge without flagging it explicitly.
```

### .claude/commands/create-content.md
```
Use model claude-sonnet-4-6.

# /create-content — Generate a post from vault notes

## SETUP — Read first
Before doing anything, read CLAUDE.md and extract:
- {{LANG}} — the vault's configured language
- {{HANDLE}} — the user's handle / name
- {{PILLARS}} — their content pillars

All output to the user must be in {{LANG}}.

---

## ABSOLUTE RULE
Never invent information. Every angle must be anchored in a vault note.
If no relevant note exists → say so and suggest running /ingest first.

---

## Step 1 — Identify the angle
If the user specified a topic → use it directly.
If not → read the 5 most recent files in 01-sources/ and propose 3 angles, one per pillar if possible.
Ask the user to pick one.

## Step 2 — Duplicate check
Search 03-content/stock/ for any similar post.
If one exists → warn the user before continuing.

## Step 3 — Find sources
Search the vault for notes relevant to the chosen angle.
Read only the summary and key sections — not full notes.

## Step 4 — Ask platform
If not specified, ask: X/Twitter or LinkedIn?

## Step 5 — Generate
Write 2 variations in the user's voice as defined in CLAUDE.md.

X/Twitter: hook + 1-3 ideas, punchy, under 1000 chars
LinkedIn: story-driven, 150-400 words, one clear narrative

## Step 6 — Save
After user validates:
Create file in 03-content/stock/ named [pillar]-[date]-[slug].md
Frontmatter: date, pillar, platform, status: ready, source: [[note]]

## Step 7 — Update context-live.md
If 06-system/context-live.md exists, increment the stock ready count.
```

### .claude/commands/weekly.md
```
Use model claude-sonnet-4-6.

# /weekly — Weekly review

## SETUP — Read first
Read CLAUDE.md and extract:
- {{LANG}} — the vault's configured language
- {{PROFILE}} — user profile
- {{HANDLE}} — user handle

All output to the user must be in {{LANG}}.

---

## Step 1 — Collect (run in parallel)
- Count files in 01-sources/ created this week
- Count files in 03-content/stock/ with status: ready
- Count files in 03-content/posts/ created this week (if folder exists)
- Read 06-system/context-live.md if it exists

## Step 2 — Write the review
Structure:
- What happened this week (sources, posts, decisions)
- Notes ingested this week (list titles)
- Content ready to publish
- Patterns and emerging themes
- Next week's top 3 priorities

## Step 3 — Save
Save as 06-system/sessions/weekly-review-[date].md

## Step 4 — Update context-live.md
If 06-system/context-live.md exists, update stock count and next week priorities.

## Step 5 — Confirm
Display: review saved, context updated, one closing sentence on focus for next week.
```

### .claude/commands/compact-sessions.md
```
Use model claude-haiku-4-5.

# /compact-sessions — Archive weekly sessions

## SETUP
Read CLAUDE.md → extract {{LANG}}. All output in {{LANG}}.

## Trigger
Run when there are 5 or more session-*.md files in 06-system/sessions/ (excluding archives/).

## Step 1 — Inventory
List all session-*.md files in 06-system/sessions/ (not in archives/).
Show count to user before doing anything.

## Step 2 — Group by week
Group by ISO week. Only process complete weeks (not the current one).

## Step 3 — Create archive
For each week: create 06-system/sessions/archives/week-YYYY-WXX.md
Content: week summary + condensed session summaries + files created.

## Step 4 — Confirm before deleting
Show the archive and ask:
A — Delete original session files
B — Keep them

## Step 5 — Confirm
Report: sessions archived, files deleted (if A), sessions remaining.
```

---

## Step 3 — Create missing template files

### templates/knowledge.md
```
---
date:
domain:
maturity: draft
---

# [Concept]

## Simple definition
[In one sentence, as if explaining to someone who doesn't know]

## Why it matters

## What I understand

## What I don't understand yet

## Sources
- [[]]
```

### templates/decision.md
```
---
date:
status: considering
---

# Decision: [title]

## Context
[Why this decision needs to be made]

## Options considered
1.
2.
3.

## Decision made

## Why

## Next action
```

### templates/project.md
```
---
date:
status: active
---

# Project: [name]

## One line
[What it is in one sentence]

## Goal
[What it needs to accomplish]

## Current state

## Next action

## Notes
```

---

## Step 4 — Create 06-system/context-live.md if missing

If 06-system/context-live.md does not exist, create it with this content:

```
---
updated: [today's date]
---

# Live context — [read Handle from CLAUDE.md]

Next action: [fill in after your first session]
Stock: 0 posts ready
Inbox: 0 files to process

## Top 3 priorities
1. Run /ingest on your first sources in 00-inbox/
2. Run /create-content to generate your first post
3. Run /weekly at the end of this week

## Quick notes
- Vault upgraded on [today's date]
- Commands available in .claude/commands/
- Templates available in templates/
```

---

## Step 5 — Add missing sections to CLAUDE.md

Read CLAUDE.md. If the following section does not exist, append it at the very end of the file:

```

## Sessions & Archives
- Each conversation is summarized in 06-system/sessions/session-YYYY-MM-DD.md
- After saving a session: count files in 06-system/sessions/ (excluding archives/)
- If count >= 5 → run /compact-sessions
- Weekly archives stored in 06-system/sessions/archives/week-YYYY-WXX.md

## Token rules
- /ingest → fast model (haiku) REQUIRED
- /query simple → fast model
- /weekly, /create-content → advanced model (sonnet)
- Maximum 3 files per /ingest session
- Never read an entire folder — grep first, read second
- Always ask before fetching a URL
```

---

## Step 6 — Final report

Display a summary of everything that was done:

✅ Created: [list of files created]
⏭ Skipped (already existed): [list of files skipped]

Then display:

Your second brain is now running the full system.

Commands available:
- /ingest — structure your inbox
- /query — search your vault
- /create-content — write a post from your notes
- /weekly — review your week
- /compact-sessions — archive old sessions

Type /ingest to get started.
