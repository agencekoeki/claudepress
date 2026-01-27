# UX System - Template

## Vue d'ensemble
Ce document définit les comportements UX du type de site.
À personnaliser pour chaque nouveau type.

## Navigation

### Structure
| Élément | Comportement |
|---------|--------------|
| Menu principal | Horizontal, en haut |
| Menu mobile | Hamburger avec overlay |
| Fil d'Ariane | Optionnel, sous le header |

### Interactions
- Hover sur liens : changement de couleur
- Page active : mise en évidence
- Sous-menus : apparition au hover/clic

## Pages

### Types de pages supportés
1. **Page standard** : Contenu libre
2. **Page d'accueil** : Template spécial avec sections

### Layouts disponibles
- `default` : Contenu centré, largeur max
- `wide` : Pleine largeur
- `sidebar` : Contenu + barre latérale

## Contenu

### Métadonnées affichées
- Date de publication : oui/non
- Auteur : oui/non
- Temps de lecture : oui/non
- Tags/catégories : oui/non

### Formatage
- Titres : ancres automatiques
- Images : lightbox optionnel
- Code : coloration syntaxique

## Interactions

### Formulaires
- Validation inline
- Messages d'erreur sous les champs
- État de chargement sur bouton submit

### Feedback utilisateur
- Toast notifications
- Modales de confirmation
- États de chargement

## Responsive

### Adaptations mobiles
- Navigation : menu hamburger
- Images : pleine largeur
- Tableaux : scroll horizontal
- Code : scroll horizontal

## Accessibilité

### Standards respectés
- WCAG 2.1 niveau AA
- Navigation au clavier
- Lecteurs d'écran supportés
