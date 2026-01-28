# Design System : [Nom du thème]

> Version: 1.0.0
> Ce document est un CONTRAT. Chaque élément DOIT être reproduit à l'identique.

## Principes de design

[Décrire les principes visuels du thème : minimaliste, bold, editorial, etc.]

---

## Tokens de référence

Voir `theme.json` pour les valeurs exactes.

---

## Composants

### Header (`header.html`)
```html
<header class="th-header">
  <div class="th-container">
    <a href="/" class="th-logo">{{site.title}}</a>
    {{>nav}}
  </div>
</header>
```

#### Spécifications
| Propriété | Valeur |
|-----------|--------|
| Hauteur | 64px |
| Background | `{{colors.background}}` |
| Border-bottom | 1px solid `{{colors.border}}` |
| Position | sticky (top: 0) après scroll de 100px |
| Z-index | 100 |

#### Classes
| Classe | Styles |
|--------|--------|
| `.th-header` | `height: 64px; border-bottom: 1px solid var(--color-border);` |
| `.th-container` | `max-width: 1200px; margin: 0 auto; padding: 0 24px; display: flex; align-items: center; justify-content: space-between;` |
| `.th-logo` | `font-size: 1.125rem; font-weight: 600; color: var(--color-text); text-decoration: none;` |

---

### Navigation (`nav.html`)
```html
<nav class="th-nav">
  <ul class="th-nav-list">
    {{#each site.navigation}}
    <li class="th-nav-item">
      <a href="{{this.url}}" class="th-nav-link{{#if this.active}} th-nav-link--active{{/if}}">
        {{this.label}}
      </a>
    </li>
    {{/each}}
  </ul>
</nav>
```

#### Classes
| Classe | Styles |
|--------|--------|
| `.th-nav-list` | `display: flex; gap: 32px; list-style: none; margin: 0; padding: 0;` |
| `.th-nav-link` | `font-size: 0.875rem; color: var(--color-text-muted); text-decoration: none; transition: color 200ms ease;` |
| `.th-nav-link:hover` | `color: var(--color-text);` |
| `.th-nav-link--active` | `color: var(--color-text); font-weight: 500;` |

---

### Footer (`footer.html`)
```html
<footer class="th-footer">
  <div class="th-container">
    <p class="th-footer-text">© {{site.year}} {{site.title}}</p>
  </div>
</footer>
```

#### Classes
| Classe | Styles |
|--------|--------|
| `.th-footer` | `padding: 48px 0; border-top: 1px solid var(--color-border); margin-top: 64px;` |
| `.th-footer-text` | `font-size: 0.875rem; color: var(--color-text-muted);` |

---

### Page Wrapper (`page-wrapper.html`)
```html
<!DOCTYPE html>
<html lang="{{site.lang}}">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{{page.title}}{{#if site.title}} | {{site.title}}{{/if}}</title>
  <meta name="description" content="{{page.description | default site.description}}">
  {{>head-extra}}
  <link rel="stylesheet" href="/assets/css/main.css">
</head>
<body class="th-body {{page.body_class}}">
  {{>header}}

  <main class="th-main">
    <div class="th-container">
      {{CONTENT}}
    </div>
  </main>

  {{>footer}}
  {{>scripts}}
</body>
</html>
```

---

### Article (`article.html`)
```html
<article class="th-article">
  <header class="th-article-header">
    <h1 class="th-article-title">{{page.title}}</h1>
    {{#if page.date}}
    <time class="th-article-date" datetime="{{page.date}}">
      {{formatDate page.date "DD MMMM YYYY"}}
    </time>
    {{/if}}
  </header>

  <div class="th-article-content th-prose">
    {{{page.content}}}
  </div>
</article>
```

---

### Typographie (classes `.th-prose`)

Ces classes s'appliquent au contenu parsé du Markdown.

| Élément | Classe | Styles principaux |
|---------|--------|-------------------|
| `h1` | `.th-h1` | `font-size: 2.25rem; font-weight: 700; line-height: 1.2; margin-bottom: 1rem;` |
| `h2` | `.th-h2` | `font-size: 1.5rem; font-weight: 600; line-height: 1.3; margin-top: 2rem; margin-bottom: 0.75rem;` |
| `h3` | `.th-h3` | `font-size: 1.25rem; font-weight: 600; line-height: 1.4; margin-top: 1.5rem; margin-bottom: 0.5rem;` |
| `p` | `.th-p` | `font-size: 1rem; line-height: 1.75; margin-bottom: 1rem;` |
| `a` | `.th-link` | `color: var(--color-accent); text-decoration: underline;` |
| `ul` | `.th-ul` | `list-style: disc; padding-left: 1.5rem; margin-bottom: 1rem;` |
| `ol` | `.th-ol` | `list-style: decimal; padding-left: 1.5rem; margin-bottom: 1rem;` |
| `li` | `.th-li` | `margin-bottom: 0.25rem;` |
| `blockquote` | `.th-blockquote` | `border-left: 3px solid var(--color-border); padding-left: 1rem; font-style: italic; color: var(--color-text-muted);` |
| `code` (inline) | `.th-code-inline` | `font-family: var(--font-mono); font-size: 0.875em; background: var(--color-surface); padding: 0.125rem 0.25rem; border-radius: 3px;` |
| `pre > code` | `.th-code-block` | `display: block; padding: 1rem; background: var(--color-surface); border-radius: 6px; overflow-x: auto;` |
| `hr` | `.th-hr` | `border: none; border-top: 1px solid var(--color-border); margin: 2rem 0;` |
| `img` | `.th-img` | `max-width: 100%; height: auto; border-radius: 6px;` |

---

## Responsive

### Breakpoints
| Nom | Min-width | Usage |
|-----|-----------|-------|
| Mobile | < 640px | Stack vertical, full-width |
| Tablet | 640px - 1023px | 2 colonnes max |
| Desktop | ≥ 1024px | Layout complet |

### Adaptations
| Composant | Mobile | Desktop |
|-----------|--------|---------|
| `.th-nav` | Menu burger | Inline |
| `.th-container` | `padding: 0 16px;` | `padding: 0 24px;` |
| `.th-h1` | `font-size: 1.875rem;` | `font-size: 2.25rem;` |

---

## États interactifs

| État | Transition | Exemple |
|------|------------|---------|
| Hover (lien) | `color 200ms ease` | Darkening |
| Hover (bouton) | `all 200ms ease` | Shadow + scale |
| Focus | `outline 2px solid accent` | Visible focus ring |
| Active | `scale(0.98)` | Légère réduction |

---

## Restrictions

### INTERDIT
- Ajouter des classes non listées ici
- Modifier les valeurs des tokens
- Utiliser des styles inline
- Utiliser des `!important`
- Importer des fonts externes non déclarées
- Utiliser des animations CSS non documentées

### OBLIGATOIRE
- Utiliser les variables CSS (`var(--color-xxx)`)
- Respecter l'ordre des propriétés dans les déclarations
- Conserver l'indentation du HTML (2 espaces)
