# Spécification : Structure des fichiers

## Conventions de nommage

### Fichiers
| Type | Convention | Exemple |
|------|------------|---------|
| Pages | kebab-case.md | `mon-article.md` |
| Composants | kebab-case.html | `article-card.html` |
| Config | camelCase.json | `site.json`, `theme.json` |
| Specs | kebab-case.md | `design-system.md` |
| Assets | kebab-case.ext | `main-style.css` |

### Dossiers
| Type | Convention | Exemple |
|------|------------|---------|
| Général | kebab-case | `my-site`, `blog-posts` |
| Privé/Interne | _préfixe | `_state`, `_template` |
| Composants | singulier | `component` pas `components` (exception acceptée) |

## Caractères autorisés
- Lettres : a-z (minuscules uniquement)
- Chiffres : 0-9
- Tiret : - (pas d'underscore dans les noms publics)
- Point : . (uniquement pour extensions)

## Caractères INTERDITS
- Espaces
- Majuscules (sauf JSON camelCase pour clés)
- Caractères spéciaux : `! @ # $ % ^ & * ( ) + = { } [ ] | \ : " ; ' < > , ? /`
- Accents : é, è, à, ù, ç, etc.
- Underscore en début (réservé aux fichiers système)

## Structure des URLs

### Règle générale : Pretty URLs
```
Source                          → Output                           → URL
content/index.md                → public/index.html                → /
content/about.md                → public/about/index.html          → /about
content/contact.md              → public/contact/index.html        → /contact
content/blog/article-1.md       → public/blog/article-1/index.html → /blog/article-1
content/blog/2024/post.md       → public/blog/2024/post/index.html → /blog/2024/post
```

### Exceptions configurables (site.json)
```json
{
  "urls": {
    "trailingSlash": true,
    "prettyUrls": true,
    "removeIndex": true
  }
}
```

## Hiérarchie de contenu

### Structure standard
```
content/
├── index.md              ← Page d'accueil
├── about.md              ← Page simple
├── contact.md            ← Page simple
├── blog/
│   ├── _index.md         ← Page listing blog (optionnel)
│   ├── article-1.md      ← Article
│   └── article-2.md      ← Article
├── services/
│   ├── _index.md         ← Page listing services
│   ├── consulting.md     ← Sous-page
│   └── training.md       ← Sous-page
└── legal/
    ├── privacy.md        ← Page légale
    └── terms.md          ← Page légale
```

### Fichiers spéciaux
| Fichier | Rôle |
|---------|------|
| `_index.md` | Page de listing pour le dossier parent |
| `_draft-*.md` | Brouillons (ignorés au build) |

## Structure des assets
```
themes/[theme]/assets/
├── css/
│   ├── main.css          ← CSS principal
│   ├── components/       ← CSS par composant (optionnel)
│   └── utilities.css     ← Classes utilitaires
├── js/
│   ├── main.js           ← JS principal
│   └── components/       ← JS par composant (optionnel)
├── fonts/
│   ├── inter-regular.woff2
│   └── inter-bold.woff2
└── images/
    ├── logo.svg
    └── icons/
        └── *.svg
```

### Assets du site (override)
```
sites/[site]/assets/       ← Assets spécifiques au site
├── images/
│   ├── hero.jpg
│   └── team/
└── documents/
    └── brochure.pdf
```

### Résolution des assets
```
1. Chercher dans sites/[site]/assets/
2. Si non trouvé → chercher dans themes/[theme]/assets/
3. Si non trouvé → ERREUR
```

## Structure output (public/)
```
public/
├── index.html
├── about/
│   └── index.html
├── blog/
│   ├── index.html        ← Listing
│   ├── article-1/
│   │   └── index.html
│   └── article-2/
│       └── index.html
├── assets/
│   ├── css/
│   │   └── main.css      ← Copié depuis theme
│   ├── js/
│   │   └── main.js
│   ├── fonts/
│   └── images/
├── robots.txt            ← Généré
├── sitemap.xml           ← Généré
└── 404.html              ← Page erreur
```

## Fichiers générés automatiquement

### robots.txt
```
User-agent: *
Allow: /

Sitemap: {{site.url}}/sitemap.xml
```

### sitemap.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
{{#each pages.all}}
  <url>
    <loc>{{absoluteUrl this.url}}</loc>
    <lastmod>{{this.date}}</lastmod>
  </url>
{{/each}}
</urlset>
```

### 404.html
Généré depuis `content/404.md` si existant, sinon template par défaut.

## Règles de copie des assets

| Source | Destination | Transformation |
|--------|-------------|----------------|
| `*.css` | Copie directe | Aucune (ou minify si prod) |
| `*.js` | Copie directe | Aucune (ou minify si prod) |
| `*.woff2` | Copie directe | Aucune |
| `*.svg` | Copie directe | Aucune |
| `*.jpg/png/webp` | Copie directe | Aucune (optimisation future) |
| `*.md` | Transformation | MD → HTML |

## Validation des chemins

Avant toute opération, vérifier :
1. Pas de `..` dans les chemins (path traversal)
2. Pas de chemins absolus commençant par `/`
3. Pas de caractères interdits
4. Fichier existe (pour lecture)
5. Dossier parent existe (pour écriture)
