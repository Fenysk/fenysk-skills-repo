---
name: create-cheat-sheet
description: >-
  Transforme un avant/après (code collé ou diff d'un commit) en fiche pattern
  concise, puis l'ajoute à un skill de référence dans fenysk-skills-repo.
  Utiliser quand l'utilisateur fournit un avant/après, référence un commit à
  documenter, ou demande d'ajouter un pattern / une bêtise à éviter à un skill
  de référence.
---

# Créer une entrée de cheat-sheet

## Charger les instructions

**Ne pas improviser le workflow.** Suivre cette séquence :

1. Appeler le MCP `user-skills-over-mcp` → outil `skill_create_cheat_sheet`
   (charge ce fichier — point d'entrée).
2. Charger le workflow complet via `read_skill_file` :
   - `slug` : `create-cheat-sheet`
   - `path` : `workflow.md`

## Répertoire cible (chemin local explicite)

Tous les fichiers créés ou modifiés vont ici, **pas** dans le projet courant :

```
C:\Users\alexi\Documents\dev\projets perso\fenysk-skills-repo\skills
```

### Vérification obligatoire avant d'écrire

Contrôler que le répertoire existe et contient au moins un skill de référence.
Fichier témoin :

```
C:\Users\alexi\Documents\dev\projets perso\fenysk-skills-repo\skills\frontend-best-practices\SKILL.md
```

- **Existe** → utiliser ce chemin.
- **N'existe pas** → ne pas écrire. Demander à l'utilisateur le chemin local
  de son clone `fenysk-skills-repo` (dossier qui contient `skills/`).
- **Chemin fourni par l'utilisateur** dans le message → l'utiliser à la place
  du chemin par défaut, puis revérifier le fichier témoin.

## Skill cible

Les skills de référence sont les dossiers sous le répertoire cible qui ont un
`SKILL.md` sommaire + un dossier `patterns/` :

- `frontend-best-practices` — React/TSX, accessibilité, structure HTML
- `tanstack-router` — navigation, scroll, loaders, SSR

Règles :

1. **Non précisé** → lister les skills disponibles et demander lequel (ou inférer
   du domaine du fix).
2. **Précisé** par l'utilisateur → utiliser ce skill.
3. Ne **pas** écrire dans `create-cheat-sheet/` (meta-skill, pas skill cible).

## Workflow résumé

1. Vérifier le chemin local (fichier témoin ci-dessus)
2. Charger `workflow.md` via MCP
3. Identifier l'entrée (avant/après collé, ou commit du projet courant)
4. Analyser les 5 points obligatoires (voir `workflow.md`)
5. Écrire `<skill-cible>/patterns/<slug>.md`
6. Mettre à jour le sommaire `<skill-cible>/SKILL.md`
