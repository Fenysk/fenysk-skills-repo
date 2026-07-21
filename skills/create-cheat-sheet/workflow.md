# Créer une entrée de cheat-sheet

Objectif : capturer une bêtise déjà faite sous forme de fiche « avant → après »
mémorisable, pour ne plus la refaire.

## Entrée : deux modes

**Mode A — avant/après fourni.** L'utilisateur colle le code fautif et le code
corrigé (ou le fautif + la description du fix). Passer directement à l'analyse.

**Mode B — commit.** L'utilisateur donne une référence de commit (hash, `HEAD`,
`HEAD~2`, ou un bout de message). Résoudre puis lire le diff :

```bash
git show <ref>                     # diff du commit par hash / ref
git log --oneline --grep="<texte>" # retrouver le commit par son message
```

Par défaut, le commit **corrige** la bêtise : « avant » = lignes `-`, « après »
= lignes `+`. Si le commit **introduit** la bêtise, inverser. Ignorer le bruit
(imports, renommages, formatage) et isoler le seul changement qui porte le sens.

## Analyse (obligatoire avant d'écrire)

Ne pas écrire la fiche tant que ces 5 points ne sont pas clairs :

1. **La bêtise** — qu'est-ce qui est faux ou fragile dans l'avant ?
2. **Le faux ami** (si pertinent) — la correction tentante mais mauvaise, et pourquoi elle ne règle rien.
3. **Le fix** — quel est le changement minimal qui corrige vraiment ?
4. **Le pourquoi** — le mécanisme qui fait que ça marche (le modèle mental).
5. **Les gotchas** — les pièges et cas limites qui subsistent.

Si un point reste incertain, poser la question avant d'écrire : une fiche
approximative est pire que pas de fiche.

## Format de la fiche (contrat)

Écrire `patterns/<slug>.md` avec EXACTEMENT cette ossature, dans cet ordre :

````markdown
# <Titre du pattern>

> **Règle :** <la règle à mémoriser en une phrase> → <nom de la solution>.

### ❌ Avant — <nom de l'anti-pattern>
```<lang>
<code minimal montrant la bêtise>
```
<conséquences en une ligne, séparées par des «  ·  »>

**Le faux ami** — <la correction tentante> :   <!-- bloc optionnel -->
```<lang>
<snippet du mauvais fix + commentaire ⚠️ pourquoi c'est faux>
```

### ✅ Après — <nom de la solution>
```<lang>
<code minimal corrigé>
```
<bénéfices en une ligne, séparés par des «  ·  »>

### Le/les <N> changement(s) qui font tout
| <quoi> | <classe / ligne> | Rôle |
|---|---|---|
| ... | ... | ... |

### Pourquoi ça marche
- <modèle mental, 2 à 3 puces max>

### Gotchas
- <pièges connus, cas limites — inclure ceux repérés dans le code lui-même>
````

Règles de rédaction :
- **Code minimal** : garder juste ce qui illustre le pattern, couper le cosmétique.
- **Avant/après en miroir** : même structure, seul le fix change → le contraste saute aux yeux.
- **Une ligne de conséquence** sous chaque bloc, jamais un paragraphe.
- **Le tableau est le cœur** : c'est ce qu'on relit à la 4e occurrence sans tout relire.
- `Pourquoi` / `Gotchas` : uniquement l'info **non déductible** du code.
- Bloc « faux ami » optionnel : l'inclure seulement s'il existe une correction
  tentante et trompeuse (ex. `stopPropagation` sur du HTML invalide).

## Intégration au skill cible

Chemin racine des skills de référence :

```
C:\Users\alexi\Documents\dev\projets perso\fenysk-skills-repo\skills
```

1. **Skill cible** — non précisé + un seul skill de référence (dossier avec
   `SKILL.md` + `patterns/`, hors `create-cheat-sheet/`) → l'utiliser.
   Plusieurs → demander lequel.
2. **Slug** en kebab-case, court et descriptif (`clickable-card`, pas
   `pattern-cartes-cliquables-avec-bouton`).
3. **Créer** `<skill-cible>/patterns/<slug>.md` avec le format ci-dessus.
4. **Ajouter une ligne au sommaire** dans `<skill-cible>/SKILL.md`, juste avant
   `<!-- Ajouter une ligne par nouveau pattern -->` :

   ```markdown
   - **<Titre court>** — <quand l'appliquer, en une phrase>.
     → [patterns/<slug>.md](patterns/<slug>.md)
   ```

5. **Vérifier** — lien à un seul niveau (`patterns/<slug>.md`), slug = lien,
   ligne de sommaire ≤ 2 lignes.

## Anti-patterns

- Ne pas dupliquer le contenu de la fiche dans le sommaire.
- Ne pas créer de sous-dossiers dans `patterns/` (un seul niveau).
- Ne pas écrire la fiche sans avoir compris le « pourquoi » : sinon on documente
  un geste sans son mécanisme, et la bêtise revient.
- Ne pas gonfler les blocs de code : une fiche illisible n'est jamais relue.
- Si `SKILL.md` dépasse ~500 lignes, proposer de regrouper par catégorie.
- Ne pas écrire dans le projet courant : les patterns vont dans
  `fenysk-skills-repo/skills/`, pas dans `.cursor/skills/` du workspace actif.
