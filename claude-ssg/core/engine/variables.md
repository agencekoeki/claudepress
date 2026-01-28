# Spécification : Variables

## Syntaxe

### Variable simple
```
{{variable}}
```

### Variable imbriquée
```
{{object.property}}
{{object.nested.deep}}
```

### Variable brute (non échappée)
```
{{{raw_html}}}
```

### Composant inclus
```
{{>component-name}}
```

### Boucle
```
{{#each array}}
    {{this}}
    {{this.property}}
    {{@index}}
    {{@first}}
    {{@last}}
{{/each}}
```

### Condition
```
{{#if condition}}...{{/if}}
{{#if condition}}...{{else}}...{{/if}}
{{#unless condition}}...{{/unless}}
```

### Comparaison
```
{{#if (eq var "value")}}...{{/if}}
{{#if (ne var "value")}}...{{/if}}
{{#if (gt var 10)}}...{{/if}}
{{#if (lt var 10)}}...{{/if}}
{{#if (gte var 10)}}...{{/if}}
{{#if (lte var 10)}}...{{/if}}
```

### Logique
```
{{#if (and condition1 condition2)}}...{{/if}}
{{#if (or condition1 condition2)}}...{{/if}}
{{#if (not condition)}}...{{/if}}
```

## Scopes de variables

### 1. `page.*` — Données de la page courante
```
page.title          ← frontmatter.title
page.content        ← contenu HTML parsé
page.date           ← frontmatter.date
page.slug           ← slug de l'URL
page.url            ← URL complète
page.path           ← chemin du fichier source
page.*              ← tout champ du frontmatter
```

### 2. `site.*` — Configuration du site
```
site.title          ← nom du site
site.description    ← description
site.url            ← URL de base
site.lang           ← langue (fr, en...)
site.author         ← auteur par défaut
site.navigation     ← array des items de nav
site.*              ← tout champ de site.json
```

### 3. `theme.*` — Tokens du thème
```
theme.name          ← nom du thème
theme.colors.*      ← palette de couleurs
theme.typography.*  ← config typo
theme.spacing.*     ← échelle d'espacement
theme.*             ← tout champ de theme.json
```

### 4. `preset.*` — Config du site-type
```
preset.name         ← nom du site-type
preset.components   ← composants requis
preset.*            ← tout champ de preset.json
```

### 5. `config.*` — Config globale
```
config.generator    ← "claude-ssg"
config.version      ← version du framework
config.buildTime    ← date/heure du build
```

### 6. `pages.*` — Collection de pages (pour listings)
```
pages.all           ← toutes les pages
pages.blog          ← pages dans content/blog/
pages.recent        ← N pages les plus récentes
```

## Helpers (fonctions)

### Formatage
```
{{formatDate page.date "DD/MM/YYYY"}}    → "27/01/2024"
{{formatDate page.date "MMMM YYYY"}}     → "janvier 2024"
{{uppercase text}}                        → "TEXTE"
{{lowercase text}}                        → "texte"
{{capitalize text}}                       → "Texte"
{{truncate text 100}}                     → "Texte tronq..."
{{slugify text}}                          → "mon-texte"
```

### URLs
```
{{absoluteUrl path}}     → "https://monsite.com/path"
{{relativeUrl path}}     → "/path"
{{assetUrl "css/x.css"}} → "/assets/css/x.css"
```

### Contenu
```
{{excerpt page.content 200}}  → Extrait de 200 caractères
{{readingTime page.content}}  → "3 min"
{{wordCount page.content}}    → 542
```

### Debug (dev only)
```
{{debug variable}}       → affiche la valeur en console
{{json variable}}        → affiche en JSON formaté
```

## Résolution des conflits

Si une variable existe dans plusieurs scopes :
```
Priorité : page > site > theme > preset > config
```

Exemple :
```
page.title = "Mon Article"
site.title = "Mon Site"

{{title}}     → Erreur (ambigu)
{{page.title}} → "Mon Article"
{{site.title}} → "Mon Site"
```

## Valeurs par défaut

Syntaxe :
```
{{variable | default "valeur par défaut"}}
```

Exemple :
```
{{page.author | default site.author | default "Anonyme"}}
```

## Échappement

Par défaut, toutes les variables sont échappées HTML :
```
page.title = "<script>alert('xss')</script>"
{{page.title}} → "&lt;script&gt;alert('xss')&lt;/script&gt;"
```

Pour du HTML brut (attention!) :
```
{{{page.content}}}
```

## Variables spéciales dans les boucles
```html
{{#each items}}
    {{@index}}    → index (0, 1, 2...)
    {{@number}}   → numéro (1, 2, 3...)
    {{@first}}    → true si premier
    {{@last}}     → true si dernier
    {{@odd}}      → true si index impair
    {{@even}}     → true si index pair
    {{this}}      → élément courant
{{/each}}
```

## Exemples concrets

### Navigation avec état actif
```html
<nav>
{{#each site.navigation}}
    <a href="{{this.url}}"
       class="th-nav-link {{#if (eq this.url page.url)}}th-nav-link--active{{/if}}">
        {{this.label}}
    </a>
{{/each}}
</nav>
```

### Liste d'articles
```html
<section class="st-article-list">
{{#each pages.blog}}
    <article class="st-article-card">
        <time datetime="{{this.date}}">{{formatDate this.date "DD MMM YYYY"}}</time>
        <h2><a href="{{this.url}}">{{this.title}}</a></h2>
        <p>{{excerpt this.content 150}}</p>
        <span class="st-reading-time">{{readingTime this.content}}</span>
    </article>
{{/each}}
</section>
```

### Condition sur le type de page
```html
{{#if (eq page.layout "blog-post")}}
    <aside class="st-sidebar">
        {{>table-of-contents}}
        {{>related-posts}}
    </aside>
{{/if}}
```
