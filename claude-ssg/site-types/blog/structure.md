# Structure du type : Blog

## Pages obligatoires

### index.md
- Layout : `homepage`
- Sections : hero, articles-recents, sidebar
- Objectif : Accueil du blog avec articles récents

### blog/_index.md
- Layout : `blog-list`
- Sections : header, article-list, pagination
- Objectif : Liste paginée de tous les articles

---

## Pages recommandées

### about.md
- Layout : `page`
- Sections : content, author-box
- Objectif : Présentation du blog/auteur

### contact.md
- Layout : `page`
- Sections : content, contact-form
- Objectif : Page de contact

---

## Pages optionnelles

### archive.md
- Layout : `archive`
- Sections : archive-list
- Objectif : Archives par année/mois

### search.md
- Layout : `page`
- Sections : search-form, search-results
- Objectif : Recherche dans le blog

---

## Structure des dossiers

```
content/
├── index.md                    ← Page d'accueil
├── about.md                    ← À propos
├── contact.md                  ← Contact
├── archive.md                  ← Archives (optionnel)
│
├── blog/
│   ├── _index.md               ← Config de la liste blog
│   ├── premier-article.md
│   ├── deuxieme-article.md
│   └── ...
│
└── pages/                      ← Autres pages statiques
    ├── mentions-legales.md
    └── politique-confidentialite.md
```

---

## Articles de blog

### Front-matter requis
```yaml
---
title: "Titre de l'article"
date: 2024-01-27
---
```

### Front-matter recommandé
```yaml
---
title: "Titre de l'article"
date: 2024-01-27
description: "Description pour SEO (160 caractères)"
author: jean-dupont
tags: [javascript, react, tutoriel]
image: /assets/images/blog/mon-article.jpg
---
```

### Front-matter complet
```yaml
---
title: "Titre de l'article"
date: 2024-01-27
updated: 2024-01-28
description: "Description pour SEO"
author: jean-dupont
tags: [javascript, react]
categories: [tutoriels]
image: /assets/images/blog/cover.jpg
imageAlt: "Description de l'image"
draft: false
featured: true
toc: true
comments: true
share: true
readingTime: 8
---
```

### Champs expliqués

| Champ | Type | Description |
|-------|------|-------------|
| `title` | string | Titre de l'article (obligatoire) |
| `date` | date | Date de publication (obligatoire) |
| `updated` | date | Date de dernière mise à jour |
| `description` | string | Meta description SEO |
| `author` | string | Slug de l'auteur |
| `tags` | array | Liste de tags |
| `categories` | array | Liste de catégories |
| `image` | string | Image de couverture |
| `imageAlt` | string | Alt text de l'image |
| `draft` | bool | Article brouillon (non publié) |
| `featured` | bool | Article mis en avant |
| `toc` | bool | Afficher table des matières |
| `comments` | bool | Activer les commentaires |
| `share` | bool | Afficher boutons de partage |
| `readingTime` | int | Temps de lecture (override auto) |

---

## Pages de listing générées

### /blog/
Liste de tous les articles avec pagination.

### /blog/page/2/
Page 2 des articles.

### /tags/
Index de tous les tags.

### /tags/javascript/
Articles tagués "javascript".

### /categories/
Index de toutes les catégories.

### /categories/tutoriels/
Articles de la catégorie "tutoriels".

### /authors/
Index de tous les auteurs.

### /authors/jean-dupont/
Articles de Jean Dupont.

---

## Fichiers de données

### _data/authors.json
```json
{
  "jean-dupont": {
    "name": "Jean Dupont",
    "slug": "jean-dupont",
    "bio": "Développeur web passionné par JavaScript",
    "avatar": "/assets/images/authors/jean.jpg",
    "email": "jean@example.com",
    "social": {
      "twitter": "@jeandupont",
      "github": "jeandupont",
      "linkedin": "jean-dupont"
    }
  }
}
```

### _data/categories.json (optionnel)
```json
{
  "tutoriels": {
    "name": "Tutoriels",
    "slug": "tutoriels",
    "description": "Guides pas à pas pour apprendre",
    "color": "#3b82f6"
  },
  "actualites": {
    "name": "Actualités",
    "slug": "actualites",
    "description": "Les dernières news du web",
    "color": "#10b981"
  }
}
```

---

## Flux générés

### /blog/feed.xml
Flux RSS 2.0 avec les 20 derniers articles.

### /blog/feed.atom
Flux Atom avec les 20 derniers articles.

---

## Sitemap

Le sitemap.xml inclut automatiquement :
- Toutes les pages
- Tous les articles
- Toutes les pages de taxonomies
- Les pages de pagination (avec priority réduite)

---

## Conventions de nommage

### Fichiers articles
```
content/blog/
├── mon-premier-article.md          ← kebab-case
├── 2024-01-27-avec-date.md         ← Date optionnelle en préfixe
└── sous-dossier/
    └── article-organise.md         ← Sous-dossiers possibles
```

### URLs générées
```
mon-premier-article.md    → /blog/mon-premier-article/
2024-01-27-avec-date.md   → /blog/avec-date/
sous-dossier/article.md   → /blog/sous-dossier/article/
```

---

## Layouts utilisés

| Page | Layout | Fallback |
|------|--------|----------|
| Article | `post` | `default` |
| Liste blog | `blog-list` | `collection-list` → `default` |
| Page tag | `taxonomy-term` | `default` |
| Index tags | `taxonomy-index` | `default` |
| Page auteur | `author` | `taxonomy-term` → `default` |
| Archives | `archive` | `default` |
