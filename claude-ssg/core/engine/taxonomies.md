# Spécification : Taxonomies & Listings

## Concepts

### Collection
Un groupe de contenus dans un même dossier.
```
content/blog/     → Collection "blog"
content/projects/ → Collection "projects"
content/recipes/  → Collection "recipes"
```

### Taxonomie
Un système de classification transversal.
```
Tags       → Mots-clés libres (many-to-many)
Categories → Classification hiérarchique (one-to-many)
Authors    → Auteurs (one-to-many)
```

### Page de listing
Une page qui liste des contenus filtrés/triés.
```
/blog/           → Tous les articles
/blog/page/2/    → Articles 11-20
/tags/js/        → Articles tagués "js"
/authors/jean/   → Articles de Jean
```

---

## Génération automatique

### Entrée
```
content/blog/
├── article-1.md (tags: [js, react])
├── article-2.md (tags: [js, php])
├── article-3.md (tags: [php, seo])
└── article-4.md (tags: [seo])
```

### Sortie générée
```
public/
├── blog/
│   ├── index.html              ← LISTING (tous les articles)
│   ├── page/2/index.html       ← PAGINATION
│   ├── article-1/index.html
│   ├── article-2/index.html
│   ├── article-3/index.html
│   └── article-4/index.html
│
├── tags/
│   ├── index.html              ← LISTING (tous les tags)
│   ├── js/index.html           ← 2 articles
│   ├── react/index.html        ← 1 article
│   ├── php/index.html          ← 2 articles
│   └── seo/index.html          ← 2 articles
│
└── categories/
    └── [idem pour les catégories]
```

---

## Configuration des collections

### Dans `site.json`
```json
{
  "collections": {
    "blog": {
      "path": "content/blog",
      "output": "blog",
      "permalink": "blog/:slug/",
      "sort": "date",
      "order": "desc",
      "pagination": {
        "enabled": true,
        "perPage": 10,
        "path": "page/:num/"
      },
      "feed": {
        "enabled": true,
        "format": ["rss", "atom"],
        "limit": 20
      },
      "taxonomies": ["tags", "categories", "authors"]
    },
    "projects": {
      "path": "content/projects",
      "output": "portfolio",
      "permalink": "portfolio/:slug/",
      "sort": "order",
      "order": "asc",
      "pagination": false,
      "taxonomies": ["technologies"]
    }
  }
}
```

### Champs de configuration

| Champ | Type | Description | Défaut |
|-------|------|-------------|--------|
| `path` | string | Dossier source | Obligatoire |
| `output` | string | Dossier de sortie | Même que path |
| `permalink` | string | Format d'URL | `:collection/:slug/` |
| `sort` | string | Champ de tri | `date` |
| `order` | string | Ordre (`asc`/`desc`) | `desc` |
| `pagination.enabled` | bool | Activer pagination | `true` |
| `pagination.perPage` | int | Items par page | `10` |
| `pagination.path` | string | Format URL pagination | `page/:num/` |
| `feed.enabled` | bool | Générer flux RSS/Atom | `true` |
| `taxonomies` | array | Taxonomies actives | `["tags"]` |

---

## Configuration des taxonomies

### Dans `site.json`
```json
{
  "taxonomies": {
    "tags": {
      "name": "Tags",
      "singular": "tag",
      "path": "tags",
      "permalink": "tags/:slug/",
      "pagination": true,
      "perPage": 20,
      "generateIndex": true
    },
    "categories": {
      "name": "Catégories",
      "singular": "category",
      "path": "categories",
      "permalink": "categories/:slug/",
      "hierarchical": true,
      "pagination": true
    },
    "authors": {
      "name": "Auteurs",
      "singular": "author",
      "path": "authors",
      "permalink": "authors/:slug/",
      "dataFile": "_data/authors.json"
    }
  }
}
```

### Fichier de données pour taxonomies enrichies

`_data/authors.json` :
```json
{
  "jean-dupont": {
    "name": "Jean Dupont",
    "slug": "jean-dupont",
    "bio": "Développeur web passionné",
    "avatar": "/assets/images/authors/jean.jpg",
    "social": {
      "twitter": "@jeandupont",
      "linkedin": "jean-dupont"
    }
  },
  "marie-martin": {
    "name": "Marie Martin",
    "slug": "marie-martin",
    "bio": "Experte SEO",
    "avatar": "/assets/images/authors/marie.jpg"
  }
}
```

---

## Front-matter des contenus

```yaml
---
title: "Mon article"
date: 2024-01-27
author: jean-dupont          # Référence à authors
tags: [javascript, react]    # Tags libres
categories: [tutoriels]      # Catégories
---
```

---

## Pages de listing générées

### Page de collection (`/blog/index.html`)

Variables disponibles :
```
{{collection.name}}        → "blog"
{{collection.items}}       → Array de tous les items
{{collection.count}}       → Nombre total
{{pagination.current}}     → Page courante (1)
{{pagination.total}}       → Nombre de pages
{{pagination.items}}       → Items de cette page
{{pagination.prev}}        → URL page précédente (null si première)
{{pagination.next}}        → URL page suivante (null si dernière)
{{pagination.pages}}       → Array de toutes les pages
```

### Page de taxonomie (`/tags/javascript/index.html`)

Variables disponibles :
```
{{taxonomy.name}}          → "Tags"
{{taxonomy.slug}}          → "tags"
{{term.name}}              → "JavaScript"
{{term.slug}}              → "javascript"
{{term.count}}             → Nombre d'items
{{term.items}}             → Array des items
{{pagination.*}}           → Même que collection
```

### Index de taxonomie (`/tags/index.html`)

Variables disponibles :
```
{{taxonomy.name}}          → "Tags"
{{taxonomy.terms}}         → Array de tous les termes
{{taxonomy.terms[].name}}  → Nom du terme
{{taxonomy.terms[].slug}}  → Slug du terme
{{taxonomy.terms[].count}} → Nombre d'items
{{taxonomy.terms[].url}}   → URL de la page du terme
```

---

## Composants de listing

### `components/article-list.html`
```html
<div class="th-article-list">
  {{#each pagination.items}}
  <article class="th-article-card">
    <time class="th-article-date">{{formatDate this.date "DD MMM YYYY"}}</time>
    <h2 class="th-article-title">
      <a href="{{this.url}}">{{this.title}}</a>
    </h2>
    <p class="th-article-excerpt">{{excerpt this.content 160}}</p>
    <footer class="th-article-meta">
      {{#if this.author}}
      <span class="th-author">Par {{this.author.name}}</span>
      {{/if}}
      {{#if this.tags}}
      <ul class="th-tag-list">
        {{#each this.tags}}
        <li><a href="{{this.url}}">{{this.name}}</a></li>
        {{/each}}
      </ul>
      {{/if}}
    </footer>
  </article>
  {{/each}}
</div>
```

### `components/pagination.html`
```html
{{#if pagination.total > 1}}
<nav class="th-pagination" aria-label="Pagination">
  {{#if pagination.prev}}
  <a href="{{pagination.prev}}" class="th-pagination-prev">
    ← Précédent
  </a>
  {{else}}
  <span class="th-pagination-prev th-disabled">← Précédent</span>
  {{/if}}

  <span class="th-pagination-info">
    Page {{pagination.current}} sur {{pagination.total}}
  </span>

  {{#if pagination.next}}
  <a href="{{pagination.next}}" class="th-pagination-next">
    Suivant →
  </a>
  {{else}}
  <span class="th-pagination-next th-disabled">Suivant →</span>
  {{/if}}
</nav>
{{/if}}
```

### `components/tag-cloud.html`
```html
<div class="th-tag-cloud">
  {{#each taxonomy.terms}}
  <a href="{{this.url}}" class="th-tag" data-count="{{this.count}}">
    {{this.name}} <span class="th-tag-count">({{this.count}})</span>
  </a>
  {{/each}}
</div>
```

---

## Layouts spécifiques

### `layouts/collection-list.html`
Template pour `/blog/index.html`

### `layouts/taxonomy-term.html`
Template pour `/tags/javascript/index.html`

### `layouts/taxonomy-index.html`
Template pour `/tags/index.html`

### Résolution automatique

Si non spécifié, Claude cherche dans cet ordre :
1. `layouts/[collection]-list.html` (ex: `blog-list.html`)
2. `layouts/collection-list.html`
3. `layouts/default.html`

---

## Fichier `_index.md` optionnel

Tu peux créer un `content/blog/_index.md` pour customiser la page de listing :
```yaml
---
title: "Notre blog"
description: "Tous nos articles sur le développement web"
layout: blog-list
pagination:
  perPage: 5
---

Bienvenue sur notre blog ! Retrouvez ici tous nos articles.
```

Le contenu Markdown est injecté AVANT la liste.

---

## Génération des flux RSS/Atom

### RSS 2.0 (`/blog/feed.xml`)
```xml
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0">
  <channel>
    <title>{{site.name}} - Blog</title>
    <link>{{site.url}}/blog/</link>
    <description>{{collection.description}}</description>
    <lastBuildDate>{{formatDate now "RFC822"}}</lastBuildDate>
    {{#each collection.items limit=20}}
    <item>
      <title>{{this.title}}</title>
      <link>{{site.url}}{{this.url}}</link>
      <description>{{excerpt this.content 300}}</description>
      <pubDate>{{formatDate this.date "RFC822"}}</pubDate>
      <guid>{{site.url}}{{this.url}}</guid>
    </item>
    {{/each}}
  </channel>
</rss>
```

### Atom (`/blog/feed.atom`)
```xml
<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title>{{site.name}} - Blog</title>
  <link href="{{site.url}}/blog/"/>
  <link href="{{site.url}}/blog/feed.atom" rel="self"/>
  <updated>{{formatDate now "ISO8601"}}</updated>
  <id>{{site.url}}/blog/</id>
  {{#each collection.items limit=20}}
  <entry>
    <title>{{this.title}}</title>
    <link href="{{site.url}}{{this.url}}"/>
    <id>{{site.url}}{{this.url}}</id>
    <updated>{{formatDate this.date "ISO8601"}}</updated>
    <summary>{{excerpt this.content 300}}</summary>
  </entry>
  {{/each}}
</feed>
```

---

## Variables de permaliens

| Variable | Description | Exemple |
|----------|-------------|---------|
| `:slug` | Slug du fichier | `mon-article` |
| `:title` | Titre slugifié | `mon-super-titre` |
| `:year` | Année (4 chiffres) | `2024` |
| `:month` | Mois (2 chiffres) | `01` |
| `:day` | Jour (2 chiffres) | `27` |
| `:collection` | Nom de la collection | `blog` |
| `:categories` | Chemin des catégories | `tech/javascript` |

### Exemples de permaliens
```
blog/:slug/                    → /blog/mon-article/
blog/:year/:month/:slug/       → /blog/2024/01/mon-article/
:categories/:slug/             → /tech/javascript/mon-article/
```

---

## Requêtes et filtres

### Dans les templates
```handlebars
{{!-- Articles récents --}}
{{#each (query "blog" limit=5 sort="date" order="desc")}}
  <li><a href="{{this.url}}">{{this.title}}</a></li>
{{/each}}

{{!-- Articles par tag --}}
{{#each (query "blog" where="tags contains 'javascript'" limit=3)}}
  <li>{{this.title}}</li>
{{/each}}

{{!-- Articles du même auteur --}}
{{#each (query "blog" where="author == page.author" exclude=page.url limit=5)}}
  <li><a href="{{this.url}}">{{this.title}}</a></li>
{{/each}}
```

### Opérateurs de filtre

| Opérateur | Description | Exemple |
|-----------|-------------|---------|
| `==` | Égal | `author == 'jean'` |
| `!=` | Différent | `draft != true` |
| `contains` | Contient (array) | `tags contains 'js'` |
| `>` `<` `>=` `<=` | Comparaison | `date >= '2024-01-01'` |

---

## Comportements automatiques

### Slugification des termes
```
"JavaScript"  → "javascript"
"C++"         → "cpp"
"Node.js"     → "nodejs"
"Développeur Web" → "developpeur-web"
```

### Comptage automatique
Chaque terme a automatiquement un `count` correspondant au nombre d'items associés.

### Tri par défaut
- Collections : par `date` décroissant
- Taxonomies index : par `count` décroissant
- Taxonomies terme : par `date` décroissant

### Exclusion des brouillons
Les contenus avec `draft: true` sont exclus des listings et des comptages.
