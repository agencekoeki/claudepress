---
name: audit
description: Analyse approfondie d'un site ou du projet
arguments:
  - name: cible
    required: false
    description: Nom du site (optionnel, sinon audit global)
  - name: --type
    required: false
    description: "Type d'audit: performance, accessibility, seo, all"
---

# Commande : audit

## But
Effectuer une analyse approfondie pour identifier les problèmes potentiels.

## Syntaxe
```
/audit
/audit [site]
/audit [site] --type=performance
```

## Types d'audit

### Performance
- Taille des fichiers HTML
- Nombre de requêtes CSS/JS
- Images non optimisées
- Code inutilisé

### Accessibilité
- Attributs alt manquants
- Contraste des couleurs
- Structure des headings
- Labels de formulaires

### SEO
- Meta descriptions
- Titres de pages
- URLs canoniques
- Structure des données

### All (défaut)
Combine tous les types d'audit.

## Sortie
```
[AUDIT] mon-blog

PERFORMANCE
  ✓ HTML moyen: 12 KB (bon)
  ⚠ 3 images > 500 KB
  ✓ CSS total: 45 KB

ACCESSIBILITÉ
  ✗ 2 images sans attribut alt
  ✓ Structure headings correcte
  ⚠ Contraste faible sur .meta-date

SEO
  ✓ Toutes les pages ont un titre
  ⚠ 1 page sans meta description
  ✓ URLs propres

Score global: 78/100

Recommandations:
1. Optimiser hero-image.jpg (1.2 MB → ~200 KB)
2. Ajouter alt sur img ligne 45 de about.md
3. Ajouter meta description à contact.md
```
