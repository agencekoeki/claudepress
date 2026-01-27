---
name: preview
description: Génère un aperçu d'une page spécifique
arguments:
  - name: site
    required: true
    description: Nom du site
  - name: page
    required: true
    description: Slug de la page à prévisualiser
---

# Commande : preview

## But
Générer et afficher un aperçu rapide d'une page sans build complet.

## Syntaxe
```
/preview [site] [page]
```

## Exemple
```
/preview mon-blog index
/preview mon-blog about
```

## Étapes d'exécution

### ÉTAPE 1 : Localisation
1. Trouver `sites/[site]/content/[page].md`
2. Si non trouvé : erreur

### ÉTAPE 2 : Génération
1. Parser uniquement cette page
2. Assembler le HTML
3. Ne pas écrire dans `public/`

### ÉTAPE 3 : Affichage
1. Afficher un résumé de la page
2. Montrer la structure générée
3. Optionnel : afficher le HTML complet

## Sortie
```
[PREVIEW] mon-blog / index

Métadonnées:
  Titre: Bienvenue sur mon blog
  Slug: index
  Template: default

Structure:
  - header (composant)
  - nav (composant)
  - heading h1: "Bienvenue sur mon blog"
  - paragraph (3)
  - image: hero.jpg
  - footer (composant)

Composants utilisés:
  ✓ page-wrapper.html (thème)
  ✓ header.html (surcharge site)
  ✓ nav.html (thème)
  ✓ heading.html (thème)
  ...

Variables résolues: 12
Taille estimée: 8.5 KB
```

## Options
- Ajouter `--html` pour afficher le code HTML complet
- Ajouter `--open` pour ouvrir dans le navigateur (si supporté)
