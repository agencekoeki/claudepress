# Spécification : Parser

## Rôle
Transformer un fichier source (Markdown + front-matter) en données structurées.

## Format d'entrée

### Front-matter YAML
```markdown
---
title: "Titre de la page"
layout: default
date: 2024-01-27
author: "Nom"
tags: [tag1, tag2]
custom_field: "valeur"
---

Contenu Markdown ici...
```

### Délimiteurs
- Début : `---` (3 tirets, première ligne du fichier)
- Fin : `---` (3 tirets)
- Tout ce qui est entre = YAML
- Tout ce qui est après = Contenu Markdown

## Format de sortie
```json
{
  "meta": {
    "source": "content/blog/mon-article.md",
    "parsed_at": "2024-01-27T14:30:00Z"
  },
  "frontmatter": {
    "title": "Titre de la page",
    "layout": "default",
    "date": "2024-01-27",
    "author": "Nom",
    "tags": ["tag1", "tag2"],
    "custom_field": "valeur"
  },
  "content": {
    "raw": "Contenu Markdown ici...",
    "html": "<p>Contenu Markdown ici...</p>"
  }
}
```

## Règles de parsing

### Front-matter
| Champ | Type | Obligatoire | Défaut |
|-------|------|-------------|--------|
| `title` | string | OUI | ERREUR si absent |
| `layout` | string | NON | `"default"` |
| `date` | date ISO | NON | date de modification fichier |
| `draft` | boolean | NON | `false` |
| `slug` | string | NON | généré depuis nom fichier |

### Markdown → HTML

#### Titres
```markdown
# H1      →  <h1 class="th-h1">...</h1>
## H2     →  <h2 class="th-h2">...</h2>
### H3    →  <h3 class="th-h3">...</h3>
#### H4   →  <h4 class="th-h4">...</h4>
##### H5  →  <h5 class="th-h5">...</h5>
###### H6 →  <h6 class="th-h6">...</h6>
```

#### Texte
```markdown
Paragraphe     →  <p class="th-p">...</p>
**bold**       →  <strong>...</strong>
*italic*       →  <em>...</em>
~~strike~~     →  <del>...</del>
`code`         →  <code class="th-code-inline">...</code>
[lien](url)    →  <a href="url" class="th-link">lien</a>
![alt](src)    →  <img src="src" alt="alt" class="th-img">
```

#### Blocs
```markdown
> quote        →  <blockquote class="th-blockquote">...</blockquote>

- item         →  <ul class="th-ul"><li class="th-li">...</li></ul>
1. item        →  <ol class="th-ol"><li class="th-li">...</li></ol>

---            →  <hr class="th-hr">
```code```    →  <pre class="th-pre"><code class="th-code-block">...</code></pre>
```

#### Tableaux
```markdown
| A | B |      →  <table class="th-table">
|---|---|           <thead class="th-thead">
| 1 | 2 |             <tr><th class="th-th">A</th><th class="th-th">B</th></tr>
                    </thead>
                    <tbody class="th-tbody">
                      <tr><td class="th-td">1</td><td class="th-td">2</td></tr>
                    </tbody>
                  </table>
```

## Gestion des erreurs

| Erreur | Comportement |
|--------|--------------|
| Pas de front-matter | ERREUR : "Front-matter manquant dans [fichier]" |
| YAML invalide | ERREUR : "YAML invalide dans [fichier] : [détail]" |
| `title` manquant | ERREUR : "Champ 'title' obligatoire dans [fichier]" |
| Markdown malformé | AVERTISSEMENT + rendu au mieux |

## Exemple complet

### Input
```markdown
---
title: "Mon premier article"
layout: blog-post
date: 2024-01-27
tags: [tech, tutorial]
---

# Introduction

Ceci est un **paragraphe** avec du texte.

## Section 1

- Item 1
- Item 2

> Une citation importante
```

### Output
```json
{
  "meta": {
    "source": "content/blog/mon-premier-article.md",
    "parsed_at": "2024-01-27T14:30:00Z"
  },
  "frontmatter": {
    "title": "Mon premier article",
    "layout": "blog-post",
    "date": "2024-01-27",
    "tags": ["tech", "tutorial"],
    "draft": false,
    "slug": "mon-premier-article"
  },
  "content": {
    "raw": "# Introduction\n\nCeci est un **paragraphe**...",
    "html": "<h1 class=\"th-h1\">Introduction</h1>\n<p class=\"th-p\">Ceci est un <strong>paragraphe</strong> avec du texte.</p>\n<h2 class=\"th-h2\">Section 1</h2>\n<ul class=\"th-ul\">\n<li class=\"th-li\">Item 1</li>\n<li class=\"th-li\">Item 2</li>\n</ul>\n<blockquote class=\"th-blockquote\">Une citation importante</blockquote>"
  }
}
```
