# UX System : Blog

> Règles d'expérience utilisateur pour les sites de type blog.

---

## Principes fondamentaux

### 1. Lisibilité avant tout
Le contenu est roi. Chaque décision UX doit favoriser la lecture.

### 2. Navigation intuitive
L'utilisateur doit pouvoir explorer le contenu facilement.

### 3. Découvrabilité
Les articles connexes doivent être facilement accessibles.

### 4. Performance
Le temps de lecture commence au chargement de la page.

---

## Page d'accueil

### Structure obligatoire
```
┌─────────────────────────────────────────┐
│  HEADER (nav, logo)                     │
├─────────────────────────────────────────┤
│  HERO (optionnel)                       │
│  - Accroche du blog                     │
│  - Article mis en avant (optionnel)     │
├─────────────────────────────────────────┤
│  ARTICLES RÉCENTS                       │
│  - 5 à 10 articles                      │
│  - Aperçu avec image, titre, extrait    │
├─────────────────────────────────────────┤
│  SIDEBAR (optionnel)                    │
│  - Catégories                           │
│  - Tags populaires                      │
│  - Newsletter                           │
├─────────────────────────────────────────┤
│  FOOTER                                 │
└─────────────────────────────────────────┘
```

### Règles
- **Maximum 10 articles** sur la page d'accueil
- **Pagination claire** vers les articles plus anciens
- **Article featured** peut être mis en avant visuellement
- **CTA newsletter** visible sans être intrusif

---

## Page article

### Structure obligatoire
```
┌─────────────────────────────────────────┐
│  HEADER                                 │
├─────────────────────────────────────────┤
│  BREADCRUMB                             │
│  Blog > Catégorie > Titre               │
├─────────────────────────────────────────┤
│  ARTICLE HEADER                         │
│  - Titre (h1)                           │
│  - Meta (date, auteur, temps lecture)   │
│  - Image de couverture (optionnel)      │
├─────────────────────────────────────────┤
│  [TABLE OF CONTENTS] (optionnel)        │
├─────────────────────────────────────────┤
│  CONTENU                                │
│  - Corps de l'article                   │
│  - Images, code, citations              │
├─────────────────────────────────────────┤
│  ARTICLE FOOTER                         │
│  - Tags                                 │
│  - Boutons de partage                   │
│  - Auteur box                           │
├─────────────────────────────────────────┤
│  ARTICLES CONNEXES                      │
│  - 3 articles similaires                │
├─────────────────────────────────────────┤
│  [COMMENTAIRES] (si activé)             │
├─────────────────────────────────────────┤
│  FOOTER                                 │
└─────────────────────────────────────────┘
```

### Règles de lisibilité

| Élément | Règle |
|---------|-------|
| Largeur du texte | 60-80 caractères max |
| Taille de police | 16px minimum (18px recommandé) |
| Interligne | 1.5 à 1.8 |
| Espacement paragraphes | 1.5em minimum |
| Contraste | WCAG AA minimum (4.5:1) |

### Règles de contenu

| Élément | Obligatoire | Règle |
|---------|-------------|-------|
| Titre h1 | Oui | Un seul, en haut |
| Date | Oui | Format lisible |
| Auteur | Recommandé | Avec lien vers profil |
| Temps de lecture | Recommandé | Estimation automatique |
| Image de couverture | Non | Ratio 16:9 ou 2:1 |
| Tags | Recommandé | Maximum 5 |
| Catégorie | Non | Une seule principale |

---

## Page liste (blog index)

### Structure
```
┌─────────────────────────────────────────┐
│  HEADER                                 │
├─────────────────────────────────────────┤
│  PAGE TITLE                             │
│  "Blog" ou "Tous les articles"          │
├─────────────────────────────────────────┤
│  [FILTRES] (optionnel)                  │
│  - Par catégorie                        │
│  - Par année                            │
├─────────────────────────────────────────┤
│  LISTE D'ARTICLES                       │
│  - 10 par page                          │
│  - Carte avec image, titre, extrait     │
├─────────────────────────────────────────┤
│  PAGINATION                             │
│  ← Précédent | Page 2/5 | Suivant →     │
├─────────────────────────────────────────┤
│  FOOTER                                 │
└─────────────────────────────────────────┘
```

### Règles
- **10 articles par page** (configurable 5-20)
- **Pagination numérotée** pour plus de 3 pages
- **Pas d'infinite scroll** (mauvais pour SEO et accessibilité)
- **Tri par date** décroissant par défaut

---

## Page taxonomie (tag, catégorie)

### Structure
```
┌─────────────────────────────────────────┐
│  HEADER                                 │
├─────────────────────────────────────────┤
│  TAXONOMY HEADER                        │
│  - Nom du tag/catégorie                 │
│  - Nombre d'articles                    │
│  - Description (optionnel)              │
├─────────────────────────────────────────┤
│  LISTE D'ARTICLES                       │
│  - Filtrés par ce terme                 │
├─────────────────────────────────────────┤
│  PAGINATION                             │
├─────────────────────────────────────────┤
│  FOOTER                                 │
└─────────────────────────────────────────┘
```

---

## Page auteur

### Structure
```
┌─────────────────────────────────────────┐
│  HEADER                                 │
├─────────────────────────────────────────┤
│  AUTHOR HEADER                          │
│  - Avatar                               │
│  - Nom                                  │
│  - Bio                                  │
│  - Réseaux sociaux                      │
├─────────────────────────────────────────┤
│  ARTICLES DE L'AUTEUR                   │
│  - Liste paginée                        │
├─────────────────────────────────────────┤
│  FOOTER                                 │
└─────────────────────────────────────────┘
```

---

## Composants UX

### Article Card
```
┌─────────────────────────┐
│  [IMAGE 16:9]           │
├─────────────────────────┤
│  CATÉGORIE              │
│  Titre de l'article     │
│  Extrait (2-3 lignes)   │
│  📅 Date  👤 Auteur     │
└─────────────────────────┘
```

Règles :
- Image optionnelle mais recommandée
- Extrait : 120-160 caractères
- Lien sur toute la carte (ou au moins le titre)
- Hover state visible

### Pagination
```
← Précédent  | 1 | 2 | [3] | 4 | 5 |  Suivant →
```

Règles :
- Toujours afficher la page courante
- Maximum 5 numéros visibles + prev/next
- Ellipsis (...) pour les pages éloignées
- Désactiver (pas cacher) les liens inactifs

### Tag Cloud
Règles :
- Maximum 20-30 tags visibles
- Taille proportionnelle au nombre d'articles (optionnel)
- Alphabétique ou par popularité
- Liens accessibles (pas juste du texte coloré)

### Author Box
```
┌──────────────────────────────────────┐
│ [AVATAR]  Nom de l'auteur            │
│           Bio courte (1-2 lignes)    │
│           🐦 📧 🔗                   │
└──────────────────────────────────────┘
```

Règles :
- Avatar : 64x64 minimum
- Bio : 160 caractères max
- Lien vers la page auteur
- Icônes réseaux sociaux accessibles

### Share Buttons
```
[Twitter] [Facebook] [LinkedIn] [Copier lien]
```

Règles :
- Maximum 4-5 réseaux
- Icônes reconnaissables
- Bouton "Copier le lien" recommandé
- Pas de compteurs (vie privée)
- Ouverture dans nouvelle fenêtre

### Table of Contents
```
Dans cet article :
├─ Introduction
├─ Première partie
│  ├─ Sous-section A
│  └─ Sous-section B
├─ Deuxième partie
└─ Conclusion
```

Règles :
- Basé sur les h2 et h3
- Sticky sidebar recommandé (desktop)
- Collapsible sur mobile
- Highlight de la section active
- Smooth scroll vers les ancres

### Reading Progress
```
████████████░░░░░░░░ 60%
```

Règles :
- Position fixe (top ou bottom)
- Fine (4-6px de hauteur)
- Couleur du thème
- Optionnel mais apprécié

---

## Interdictions

### Ne jamais faire

| Interdit | Raison |
|----------|--------|
| Popup newsletter immédiate | Interrompt la lecture |
| Publicités dans le contenu | Casse le flux de lecture |
| Autoplay vidéo/audio | Intrusif |
| Infinite scroll sans URL | Mauvais SEO, pas de retour |
| Liens cachés | Accessibilité |
| Texte sur image sans contraste | Illisible |
| Plus de 3 niveaux de menu | Complexité |

### Popup newsletter acceptable
- Après 60 secondes OU
- Après 50% de scroll OU
- À l'intention de sortie (exit intent)
- Fermable facilement
- Cookie "ne plus afficher" respecté

---

## Mobile

### Règles spécifiques
- Police : 16px minimum (pas de zoom iOS)
- Boutons : 44x44px minimum
- Espacement touch : 8px entre éléments cliquables
- Menu hamburger si > 4 items nav
- Pas de hover-only interactions
- TOC collapsé par défaut

### Ordre des éléments
Sur mobile, la sidebar passe sous le contenu principal.

---

## Performance

### Objectifs
| Métrique | Cible |
|----------|-------|
| LCP (Largest Contentful Paint) | < 2.5s |
| FID (First Input Delay) | < 100ms |
| CLS (Cumulative Layout Shift) | < 0.1 |

### Bonnes pratiques
- Images lazy loaded
- Format WebP avec fallback
- Fonts avec font-display: swap
- Critical CSS inline
- JavaScript différé

---

## Accessibilité

### Obligatoire
- Structure de titres logique (h1 → h2 → h3)
- Alt text sur toutes les images
- Labels sur les formulaires
- Focus visible sur tous les éléments interactifs
- Skip link vers le contenu
- Contraste suffisant (WCAG AA)

### Recommandé
- Navigation au clavier complète
- ARIA landmarks
- Articles avec balise `<article>`
- Temps de lecture annoncé
