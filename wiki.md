# Guide du vault

## 00-inbox/
Sources brutes : articles, tweets, vidéos, docs, notes de réunion.
**Règle :** on colle ici sans modifier. On lance `/ingest` pour traiter.

## 01-sources/
Notes structurées après ingestion. Chaque note = une source traitée avec :
- Résumé en 3 points
- Citation clé
- Ce que tu en retiens personnellement

## 02-knowledge/
Concepts que tu as vraiment compris et synthétisés.
Ici, c'est ta pensée — pas un résumé d'article.

## 03-content/
- `stock/` → posts prêts à publier (`status: ready` dans le frontmatter)
- `posts/` → posts déjà publiés (archive)

## 04-decisions/
Décisions importantes documentées : contexte, options considérées, verdict, pourquoi.
Utile pour ne pas re-débattre ce qu'on a déjà tranché.

## 05-projects/
Un fichier par projet actif. État actuel + prochaine action.

## 06-system/
Système interne — ne pas modifier manuellement.
- `sessions/` → résumé de chaque conversation avec Claude
- `sessions/archives/` → archives hebdomadaires compactées

## templates/
Modèles de notes. Copier-coller pour créer une nouvelle note structurée.
