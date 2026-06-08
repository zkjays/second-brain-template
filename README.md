# Second Brain Template — Free Version

A personal knowledge system powered by Claude AI.
You clip, Claude structures. You ask, Claude answers from your own notes.

---

## Download

Click the green "Code" button → "Download ZIP" → extract the folder anywhere on your machine.

Or with git : `git clone https://github.com/zkjays/second-brain-template.git`

---

## What you get

```
your-second-brain/
├── CLAUDE.md            ← fill this in first
├── 00-inbox/            → paste everything here
├── 01-sources/          → structured notes (Claude writes here)
├── 02-knowledge/        → concepts you've mastered
├── 03-content/          → post drafts and published archive
├── 04-decisions/        → your important calls, documented
├── 05-projects/         → one file per active project
├── 06-system/           → sessions, live context
└── templates/           → note templates
    ├── source.md
    └── content-post.md
```

---

## Setup (~15 min, all free)

### 1. Obsidian — your reading room
1. Download : obsidian.md/download
2. Open Obsidian → "Open folder as vault"
3. Select the folder you just downloaded

### 2. A terminal — where Claude works
- VS Code : download code.visualstudio.com → File → Open Folder → select your vault → open the integrated terminal
- Or use any terminal (Windows Terminal, iTerm, PowerShell) and navigate to the folder

### 3. Claude Code — the agent
1. In the terminal : `npm install -g @anthropic-ai/claude-code`
2. Launch : `claude`
3. Connect your account at claude.ai

---

## First steps

Once Claude Code is running in your vault :

1. Open CLAUDE.md → fill in the fields marked [FILL IN]
2. Paste any article or tweet into 00-inbox/
3. Type /ingest → Claude structures it into 01-sources/
4. Type /create-content → Claude writes a post from your notes

---

## Want the full system?

The free version gives you the structure.
The complete version gives you the system that runs itself :

- Automatic setup (Claude configures everything from 6 questions)
- 5 pre-built commands (/ingest, /query, /weekly, /create-content, /compact-sessions)
- Token economy rules (costs less to run)
- Example files in every folder
- context-live.md — instant session recovery

Available for builders at thedarkroom.xyz

---

## Questions?

X : @zkjays
GitHub Issues : github.com/zkjays/second-brain-template
