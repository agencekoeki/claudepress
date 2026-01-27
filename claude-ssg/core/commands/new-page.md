---
name: new-page
description: Crée une nouvelle page dans un site
arguments:
  - name: site
    required: true
    description: Nom du site cible
  - name: titre
    required: true
    description: Titre de la page
  - name: --template
    required: false
    description: Template de contenu à utiliser
---

# Commande : new-page

## But
Créer une nouvelle page Markdown dans un site existant.

## Syntaxe
```
/new-page [site] "[titre]"
/new-page [site] "[titre]" --template=[template]
```

## Exemple
```
/new-page mon-blog "À propos de nous"
/new-page mon-blog "Article Test" --template=blog-post
```

## Pré-requis
- Le site doit exister
- Le slug généré ne doit pas déjà exister

## Étapes d'exécution

### ÉTAPE 1 : Génération du slug
1. Convertir le titre en slug : "À propos de nous" → "a-propos-de-nous"
2. Vérifier l'unicité du slug
3. Si conflit : ajouter un suffixe numérique

### ÉTAPE 2 : Création du fichier
1. Si template spécifié : charger depuis `site-types/[type]/content-templates/`
2. Sinon : utiliser le template par défaut
3. Remplir le frontmatter avec le titre et slug
4. Créer le fichier dans `sites/[site]/content/`

### ÉTAPE 3 : Confirmation
Afficher le chemin du fichier créé.

## Template par défaut
```markdown
---
title: "[titre]"
slug: "[slug]"
date: "[date-du-jour]"
---

# [titre]

Contenu de la page...
```

## Fichier créé
```
sites/[site]/content/[slug].md
```
