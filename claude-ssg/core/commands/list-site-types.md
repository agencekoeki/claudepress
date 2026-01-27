---
name: list-site-types
description: Liste tous les types de sites disponibles
arguments: none
---

# Commande : list-site-types

## But
Afficher la liste de tous les types de sites disponibles avec leurs informations.

## Syntaxe
```
/list-site-types
```

## Sortie
```
[TYPES DE SITES DISPONIBLES]

blog
  Description: Site de blog avec articles et catégories
  Composants spécifiques: 3
  Templates de contenu: 2 (article, page)

portfolio
  Description: Portfolio pour présenter des projets
  Composants spécifiques: 5
  Templates de contenu: 1 (projet)

documentation
  Description: Site de documentation technique
  Composants spécifiques: 4
  Templates de contenu: 3 (page, api-ref, tutorial)

_template
  (Template de base - ne pas utiliser directement)

Total: 3 types de sites utilisables
```

## Informations affichées
Pour chaque type :
- Nom
- Description
- Nombre de composants spécifiques
- Templates de contenu disponibles

## Utilisation
Utiliser cette commande pour :
- Voir les types disponibles avant `/init-site`
- Comprendre la structure de chaque type
- Choisir le bon type pour un nouveau projet
