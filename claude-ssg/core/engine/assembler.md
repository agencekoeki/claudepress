# Spécification : Assembler

## Rôle
Combiner les composants HTML avec les données parsées pour produire une page HTML complète.

## Processus d'assemblage

### Étape 1 : Charger le contexte
```
1. Lire site.json → variable `site`
2. Lire theme.json → variable `theme`
3. Lire preset.json → variable `preset`
4. Lire config globales → variable `config`
5. Parser le fichier source → variable `page`
```

### Étape 2 : Déterminer le layout
```
1. Vérifier page.frontmatter.layout
2. Si défini → utiliser ce layout
3. Sinon → utiliser "default"
4. Chercher le layout dans :
   a. sites/[site]/overrides/components/[layout].html
   b. site-types/[type]/components/[layout].html
   c. themes/[theme]/components/page-wrapper.html
```

### Étape 3 : Charger les composants
```
Pour chaque composant nécessaire :
1. Chercher dans sites/[site]/overrides/components/
2. Si non trouvé → chercher dans site-types/[type]/components/
3. Si non trouvé → chercher dans themes/[theme]/components/
4. Si non trouvé → ERREUR
```

### Étape 4 : Résoudre les variables
```
Ordre de résolution (priorité décroissante) :
1. page.frontmatter.* (données de la page)
2. site.* (config du site)
3. theme.tokens.* (tokens du thème)
4. preset.* (config du site-type)
5. config.* (config globale)
```

### Étape 5 : Assembler
```
1. Prendre le page-wrapper (template de base)
2. Injecter header
3. Injecter navigation
4. Injecter contenu (page.content.html)
5. Injecter footer
6. Résoudre toutes les {{variables}}
7. Nettoyer (supprimer lignes vides multiples)
```

### Étape 6 : Valider
```
1. Vérifier qu'aucune {{variable}} non résolue
2. Vérifier structure HTML valide
3. Vérifier classes CSS conformes au design-system
```

## Structure d'une page assemblée
```html
<!DOCTYPE html>
<html lang="{{site.lang}}">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{{page.title}} | {{site.title}}</title>
    <meta name="description" content="{{page.description}}">
    {{HEAD_EXTRA}}
    <link rel="stylesheet" href="/assets/css/style.css">
</head>
<body class="{{page.body_class}}">
    {{HEADER}}

    <main class="th-main">
        {{CONTENT}}
    </main>

    {{FOOTER}}

    {{SCRIPTS}}
</body>
</html>
```

## Zones d'injection

| Zone | Description | Source |
|------|-------------|--------|
| `{{HEAD_EXTRA}}` | Meta tags, fonts, etc. | site.json + page.frontmatter |
| `{{HEADER}}` | Header du site | components/header.html |
| `{{CONTENT}}` | Contenu principal | page.content.html |
| `{{FOOTER}}` | Footer du site | components/footer.html |
| `{{SCRIPTS}}` | Scripts JS | site.json |

## Composants imbriqués

Les composants peuvent inclure d'autres composants avec la syntaxe :
```html
{{>component-name}}
```

Exemple dans `header.html` :
```html
<header class="th-header">
    <div class="th-container">
        <a href="/" class="th-logo">{{site.title}}</a>
        {{>nav}}
    </div>
</header>
```

## Boucles

Syntaxe pour itérer :
```html
{{#each items}}
    <li>{{this.name}}</li>
{{/each}}
```

Exemple pour navigation :
```html
<ul class="th-nav-list">
{{#each site.navigation}}
    <li class="th-nav-item">
        <a href="{{this.url}}" class="th-nav-link{{#if this.active}} th-nav-link--active{{/if}}">
            {{this.label}}
        </a>
    </li>
{{/each}}
</ul>
```

## Conditions

Syntaxe :
```html
{{#if condition}}
    HTML si vrai
{{else}}
    HTML si faux
{{/if}}
```

Exemple :
```html
{{#if page.show_author}}
    <p class="th-author">Par {{page.author}}</p>
{{/if}}
```

## Gestion des erreurs

| Erreur | Comportement |
|--------|--------------|
| Composant non trouvé | ERREUR BLOQUANTE |
| Variable non résolue | ERREUR BLOQUANTE |
| Layout non trouvé | ERREUR BLOQUANTE |
| Boucle sur non-array | ERREUR BLOQUANTE |

## Output

Le fichier HTML final est écrit dans :
```
public/[slug]/index.html
```

Avec mise à jour du manifest.
