---
name: tanstack-router
description: >-
  Recueil de patterns TanStack Router (navigation, scroll, loaders, SSR)
  sous forme de cheat-sheet. Utiliser quand on configure le routeur, une route
  ou une navigation et qu'on veut appliquer le comportement documenté plutôt
  qu'une solution ad-hoc.
---

# TanStack Router

Sommaire des patterns disponibles. Chaque ligne indique quand l'appliquer.
Lire le fichier correspondant dans `patterns/` pour le détail et l'exemple de code.

- **Scroll restoration par route** — `scrollRestoration: true` est global ; besoin de ne pas remonter en haut, de ne pas restaurer au retour arrière, ou de gérer une page à scroll infini. → [patterns/scroll-restoration.md](patterns/scroll-restoration.md)
- **Ordre `loader` avant `head`** — `head` lit `loaderData` et TS dit `never` / `useLoaderData()` est `| undefined`. → [patterns/loader-before-head.md](patterns/loader-before-head.md)

<!-- Ajouter une ligne par nouveau pattern -->
