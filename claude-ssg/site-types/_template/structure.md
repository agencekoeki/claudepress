# Structure - Template

## Organisation des pages

### Hiérarchie par défaut
```
/                       → index.md (page d'accueil)
/about                  → about.md
/contact                → contact.md
/[page]                 → [page].md
```

## Structure des URLs

### Conventions
- Tout en minuscules
- Mots séparés par des tirets
- Pas d'extension .html visible
- Caractères spéciaux normalisés

### Exemples
| Fichier | URL |
|---------|-----|
| `index.md` | `/` |
| `about.md` | `/about` |
| `mon-article.md` | `/mon-article` |
| `posts/premier.md` | `/posts/premier` |

## Navigation automatique

### Génération du menu
Le menu est généré à partir de :
1. `navigation.items` dans `site.json` (si défini)
2. Ou automatiquement depuis les pages avec `menu: true` dans le frontmatter

### Ordre des éléments
1. Par `order` dans le frontmatter (si défini)
2. Par ordre alphabétique du titre

## Templates de pages

### Variables disponibles dans toutes les pages
```yaml
---
title: "Titre de la page"           # Requis
slug: "mon-slug"                    # Auto-généré si absent
description: "Meta description"     # Optionnel
template: "default"                 # Optionnel
menu: true                          # Inclure dans la nav
order: 1                            # Ordre dans la nav
---
```

## Zones de contenu

### Structure d'une page
```
┌─────────────────────────────────┐
│           Header                │
├─────────────────────────────────┤
│           Navigation            │
├─────────────────────────────────┤
│                                 │
│           Contenu               │
│           Principal             │
│                                 │
├─────────────────────────────────┤
│           Footer                │
└─────────────────────────────────┘
```
