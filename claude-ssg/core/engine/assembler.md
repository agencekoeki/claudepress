# Assembler - Moteur d'assemblage HTML

## Rôle
Assembler les composants HTML pour générer les pages finales.

## Processus d'assemblage

### Étape 1 : Chargement du template
1. Charger `page-wrapper.html` du thème
2. Identifier les zones à remplir : `{{slot:header}}`, `{{slot:content}}`, `{{slot:footer}}`

### Étape 2 : Résolution des slots
Pour chaque slot :
1. Charger le composant correspondant
2. Résoudre les variables internes
3. Insérer dans le template

### Étape 3 : Injection du contenu
1. Convertir chaque bloc Markdown en HTML via son composant
2. Concaténer tous les blocs
3. Injecter dans `{{slot:content}}`

### Étape 4 : Résolution finale
1. Résoudre toutes les variables restantes
2. Nettoyer les variables non résolues (optionnel selon config)
3. Minifier si configuré

## Syntaxe des slots

Dans les templates :
```html
<header>
    {{slot:header}}
</header>
<main>
    {{slot:content}}
</main>
<footer>
    {{slot:footer}}
</footer>
```

## Syntaxe des variables

```html
<!-- Variable simple -->
<title>{{page.title}}</title>

<!-- Variable avec fallback -->
<meta name="description" content="{{page.description|Site description}}">

<!-- Variable conditionnelle -->
{{#if page.image}}
<meta property="og:image" content="{{page.image}}">
{{/if}}
```

## Inclusion de composants

```html
<!-- Inclusion simple -->
{{include:nav}}

<!-- Inclusion avec paramètres -->
{{include:button text="Submit" type="primary"}}

<!-- Boucle sur une liste -->
{{#each navigation.items}}
    {{include:nav-item label="{{this.label}}" href="{{this.href}}"}}
{{/each}}
```

## Fichier de sortie

Le fichier HTML final est écrit dans :
`sites/[site]/public/[slug].html`

Ou pour l'index :
`sites/[site]/public/index.html`
