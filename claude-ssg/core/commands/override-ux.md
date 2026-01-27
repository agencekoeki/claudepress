---
name: override-ux
description: Personnalise les comportements UX pour un site
arguments:
  - name: site
    required: true
    description: Nom du site
---

# Commande : override-ux

## But
Ouvrir et personnaliser le fichier de tweaks UX d'un site.

## Syntaxe
```
/override-ux [site]
```

## Exemple
```
/override-ux mon-blog
```

## Fichier concerné
```
sites/[site]/overrides/ux-tweaks.md
```

## Contenu type du fichier
```markdown
# UX Tweaks - mon-blog

## Navigation
- Menu sticky: oui
- Animation au scroll: fade-in

## Articles
- Afficher date: oui
- Afficher auteur: non
- Temps de lecture: oui

## Footer
- Afficher réseaux sociaux: oui
- Newsletter: non

## Animations
- Transitions: 0.3s ease
- Hover effects: scale(1.02)
```

## Utilisation
Ce fichier permet de personnaliser des comportements UX sans toucher aux composants :
- Activer/désactiver des fonctionnalités
- Ajuster des paramètres visuels
- Personnaliser des textes

## Notes
- Les tweaks sont lus par les composants du type de site
- Tous les types de sites ne supportent pas tous les tweaks
- Consulter `site-types/[type]/ux-system.md` pour les options disponibles
