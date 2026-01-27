# Variables - Système de variables

## Types de variables

### 1. Variables globales (site.json)
Définies dans `sites/[site]/site.json` :
```json
{
    "name": "Mon Site",
    "url": "https://example.com",
    "language": "fr",
    "author": "Nom Auteur"
}
```
Accès : `{{site.name}}`, `{{site.url}}`, etc.

### 2. Variables de page (frontmatter)
Définies dans le frontmatter de chaque page :
```yaml
---
title: "Ma Page"
description: "Description"
custom: "Valeur"
---
```
Accès : `{{page.title}}`, `{{page.custom}}`, etc.

### 3. Variables de thème (theme.json)
Définies dans `themes/[theme]/theme.json` :
```json
{
    "colors": {
        "primary": "#007bff",
        "secondary": "#6c757d"
    }
}
```
Accès : `{{theme.colors.primary}}`, etc.

### 4. Variables de build (automatiques)
Générées automatiquement :
- `{{build.date}}` : Date ISO de génération
- `{{build.timestamp}}` : Timestamp Unix
- `{{build.version}}` : Numéro de version incrémental

### 5. Variables d'environnement
Préfixées par `env.` :
- `{{env.NODE_ENV}}` : development/production
- `{{env.BASE_URL}}` : URL de base (peut différer selon l'env)

## Syntaxe avancée

### Valeur par défaut (fallback)
```
{{variable|valeur par défaut}}
```

### Condition
```
{{#if variable}}
    Contenu si variable existe et n'est pas vide
{{/if}}

{{#if variable}}
    Si vrai
{{else}}
    Si faux
{{/if}}
```

### Boucle
```
{{#each items}}
    {{this.property}}
    {{@index}} <!-- Index de l'itération -->
    {{@first}} <!-- true si premier élément -->
    {{@last}} <!-- true si dernier élément -->
{{/each}}
```

### Échappement
Pour afficher les accolades sans interprétation :
```
\{{ceci ne sera pas interprété}}
```

## Résolution

Ordre de priorité (le premier trouvé gagne) :
1. Variables de page
2. Variables de site
3. Variables de thème
4. Variables de build
5. Variables d'environnement
6. Valeur par défaut (si spécifiée)
7. Chaîne vide (ou erreur selon config)
