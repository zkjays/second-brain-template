# Second Brain Template — Version Gratuite

Un système de notes personnel piloté par Claude AI.
Tu clippes, Claude structure. Tu interroges, Claude répond depuis tes propres notes.

---

## Ce que tu as ici

```
ton-vault/
├── 00-inbox/        → où tu colles tout ce que tu veux traiter
├── 01-sources/      → notes structurées après ingestion
├── 02-knowledge/    → concepts que tu as vraiment compris
├── 03-content/
│   ├── stock/       → posts prêts à publier
│   └── posts/       → posts déjà publiés
├── 04-decisions/    → tes décisions importantes documentées
├── 05-projects/     → un fichier par projet actif
├── 06-system/       → sessions, contexte live
└── templates/       → modèles de notes
```

---

## Installation (15 minutes)

### 1. Obsidian — ton vault

1. Télécharge [obsidian.md](https://obsidian.md)
2. Ouvre l'app → "Open folder as vault"
3. Sélectionne le dossier que tu viens de télécharger

### 2. VSCode — là où Claude travaille

1. Télécharge [code.visualstudio.com](https://code.visualstudio.com)
2. File → Open Folder → sélectionne ton vault

### 3. Claude Code — l'agent

1. Dans le terminal VSCode : `npm install -g @anthropic-ai/claude-code`
2. Lance : `claude`
3. Connecte ton compte [claude.ai](https://claude.ai)

---

## Tes premières actions

Une fois Claude Code lancé dans ton vault :

1. **Configure ton identité** → ouvre `CLAUDE.md` et remplis les champs `[À REMPLIR]`
2. **Colle une source** → copie un article ou tweet dans `00-inbox/` et dis à Claude : `/ingest`
3. **Génère un post** → depuis la note ingérée, dis : `/create-content`

---

## La différence avec la version complète

La version gratuite te donne la structure.
La version complète te donne le système qui tourne :

- Setup automatique (Claude configure tout depuis 6 questions)
- 5 commandes prêtes (`/ingest`, `/query`, `/weekly`, `/create-content`, `/compact-sessions`)
- Règles d'économie de tokens (moins cher à utiliser)
- Fichiers exemples dans chaque dossier
- `context-live.md` — reprise instantanée entre sessions

Disponible pour les builders de [THE DARKROOM](https://thedarkroom.xyz).

---

## Questions ?

GitHub Issues : [github.com/zkjays/second-brain-template](https://github.com/zkjays/second-brain-template)
X : [@zkjays](https://x.com/zkjays)
