---
name: status
description: Affiche l'état actuel du projet et des sites
arguments:
  - name: site
    required: false
    description: Nom d'un site spécifique (optionnel)
---

# Commande : status

## But
Afficher un résumé de l'état du projet ou d'un site spécifique.

## Syntaxe
```
/status
/status [site]
```

## Sortie globale (/status)
```
[STATUS] Claude SSG

Thèmes disponibles : 2
  - minimal (v1.0.0)
  - corporate (v1.2.0)

Types de sites : 3
  - blog
  - portfolio
  - documentation

Sites : 2
  - mon-blog (thème: minimal, type: blog)
    → Dernière build: 2024-01-15 14:30
    → 5 pages
  - docs (thème: minimal, type: documentation)
    → Dernière build: jamais
    → 12 pages
```

## Sortie spécifique (/status [site])
```
[STATUS] mon-blog

Configuration
  Thème: minimal
  Type: blog
  URL: https://mon-blog.example.com

Contenu
  Pages: 5
  - index.md (modifié: 2024-01-15)
  - about.md (modifié: 2024-01-10)
  - contact.md (modifié: 2024-01-08)
  - posts/premier-article.md (modifié: 2024-01-15)
  - posts/deuxieme-article.md (modifié: 2024-01-14)

Surcharges actives
  Composants: 1 (header.html)
  UX Tweaks: oui

Build
  Dernière: 2024-01-15 14:30:22
  Pages générées: 5
  Taille totale: 125 KB

État: À JOUR (aucun changement depuis le dernier build)
```

## États possibles
- `À JOUR` : Aucune modification depuis le dernier build
- `MODIFIÉ` : Des fichiers ont changé, rebuild nécessaire
- `JAMAIS CONSTRUIT` : Aucun build effectué
- `ERREUR` : Configuration invalide
