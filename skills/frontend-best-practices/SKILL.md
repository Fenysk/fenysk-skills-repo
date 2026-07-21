---
name: frontend-best-practices
description: >-
  Recueil de bonnes pratiques frontend (React/TSX, accessibilité, structure
  HTML) sous forme de patterns réutilisables. Utiliser quand on écrit ou
  révise un composant frontend et qu'on veut appliquer un pattern éprouvé
  plutôt qu'une solution ad-hoc.
---

# Bonnes pratiques frontend

Sommaire des patterns disponibles. Chaque ligne indique quand l'appliquer.
Lire le fichier correspondant dans `patterns/` pour le détail et l'exemple de code.

- **Cartes cliquables avec actions imbriquées** — carte qui navigue au clic, contenant un bouton (like, menu…) qui doit rester cliquable indépendamment. → [patterns/clickable-card.md](patterns/clickable-card.md)
- **`enum` pour un état simple** — statut de formulaire ou petit set de valeurs fixes, sans besoin de nombres ni d'itération runtime. → [patterns/enum-vs-const-union.md](patterns/enum-vs-const-union.md)
- **Shell plein viewport sous le header** — layout app (header + zone contenu) qui doit occuper toute la hauteur d’écran. → [patterns/full-height-app-shell.md](patterns/full-height-app-shell.md)
- **Espace JSX + texte conditionnel** — label fixe + suffixe optionnel : éviter l’espace orphelin invisible (`white-space: normal`). → [patterns/jsx-trailing-whitespace.md](patterns/jsx-trailing-whitespace.md)
- **Effets hors updater `setState`** — log / fetch / mutation dans un `setState(fn)` qui se double en Strict Mode (dev). → [patterns/pure-setstate-updater.md](patterns/pure-setstate-updater.md)

<!-- Ajouter une ligne par nouveau pattern -->