# Design System - Template

## Vue d'ensemble
Ce document définit le système de design du thème.
À personnaliser pour chaque nouveau thème.

## Couleurs

### Palette principale
| Nom | Valeur | Utilisation |
|-----|--------|-------------|
| Primary | `#007bff` | Actions principales, liens |
| Secondary | `#6c757d` | Actions secondaires |
| Background | `#ffffff` | Fond de page |
| Text | `#212529` | Texte principal |

### États
| État | Couleur |
|------|---------|
| Success | `#28a745` |
| Danger | `#dc3545` |
| Warning | `#ffc107` |
| Info | `#17a2b8` |

## Typographie

### Famille de polices
- **Corps** : System UI stack (natif)
- **Code** : Monospace stack

### Échelle
| Niveau | Taille | Utilisation |
|--------|--------|-------------|
| H1 | 2.5rem | Titre principal |
| H2 | 2rem | Sections majeures |
| H3 | 1.75rem | Sous-sections |
| H4 | 1.5rem | Titres mineurs |
| H5 | 1.25rem | Labels importants |
| H6 | 1rem | Labels |
| Body | 1rem | Texte courant |
| Small | 0.875rem | Notes, meta |

## Espacements

Basé sur une unité de 8px :
- `xs` : 4px
- `sm` : 8px
- `md` : 16px
- `lg` : 32px
- `xl` : 64px

## Composants

Voir le dossier `components/` pour la liste complète.
Chaque composant suit ces principes :
1. Autonomie : fonctionne seul
2. Personnalisation : via variables
3. Accessibilité : ARIA quand nécessaire

## Responsive

Breakpoints :
- Mobile : < 576px
- Tablet : 576px - 768px
- Desktop : 768px - 992px
- Wide : > 992px
