# Espace JSX + texte conditionnel

> **Règle :** un espace avant `{condition}` devient un espace orphelin quand c’est falsy — le mettre **dans** la branche truthy → séparateur conditionnel.

### ❌ Avant — séparateur hors condition
```tsx
<button>
  Say Hello {reply && `- ${reply}`}
</button>
```
Espace source après `Hello` même si `reply` est vide · invisible à l’œil (`white-space: normal`) · sélection / inspecteur trompeurs.

**Le faux ami** — conclure « pas d’espace » parce qu’on ne le sélectionne pas :
```tsx
// Sélection s’arrête sur le "o" → ⚠️ ne prouve rien
// white-space: normal collapse les espaces de fin de boîte
JSON.stringify(button.textContent) // souvent "Say Hello " avec l’espace
```

### ✅ Après — séparateur dans la branche truthy
```tsx
<button>
  Say Hello{reply ? ` - ${reply}` : null}
</button>
```
Pas d’espace orphelin · séparateur uniquement quand il y a une réponse · texte DOM = ce qu’on voit.

### Les 2 changements qui font tout
| Quoi | Où | Rôle |
|---|---|---|
| Pas d’espace avant `{…}` | texte fixe `Say Hello` | évite l’espace de fin quand `reply` est vide |
| ` - ` dans le template | branche truthy `` ` - ${reply}` `` | séparateur seulement si contenu |

### Pourquoi ça marche
- Avec `white-space: normal` (défaut), un espace en **fin** de boîte de ligne n’occupe pas de place visuelle et est quasi non sélectionnable — d’où l’illusion « pas dans le DOM ».
- `textContent` / `JSON.stringify(…)` révèlent encore cet espace ; l’UI et la sélection, non.
- En collant le séparateur dans le ternaire, le nœud texte fixe s’arrête à `Hello` : plus rien à collapse.

### Gotchas
- `0 && "x"` affiche `0` (falsy mais rendu) — préférer `reply ? … : null` pour du texte.
- `white-space: pre` / `pre-wrap` ferait **réapparaître** l’espace orphelin à l’écran.
- Vérif rapide : `JSON.stringify($0.textContent)` et `.length` dans la console.
