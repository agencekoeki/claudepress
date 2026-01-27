---
name: validate
description: Valide un site sans le construire
arguments:
  - name: site
    required: true
    description: Nom du site à valider
---

# Commande : validate

## But
Vérifier qu'un site est correctement configuré et prêt à être construit.

## Syntaxe
```
/validate [site]
```

## Exemple
```
/validate mon-blog
```

## Vérifications effectuées

### 1. Configuration (site.json)
- [ ] Le fichier existe et est un JSON valide
- [ ] Les champs requis sont présents
- [ ] Le thème référencé existe
- [ ] Le type de site référencé existe

### 2. Contenu
- [ ] Au moins une page existe dans `content/`
- [ ] Tous les fichiers .md ont un frontmatter valide
- [ ] Tous les slugs sont uniques

### 3. Composants
- [ ] Tous les composants référencés existent
- [ ] La syntaxe HTML des composants est valide

### 4. Variables
- [ ] Toutes les variables utilisées sont définies
- [ ] Pas de références circulaires

### 5. Assets
- [ ] Tous les assets référencés existent
- [ ] Pas de fichiers trop volumineux (warning)

## Sortie
```
[VALIDATION] mon-blog

Configuration
  ✓ site.json valide
  ✓ Thème 'minimal' trouvé
  ✓ Type 'blog' trouvé

Contenu
  ✓ 5 pages trouvées
  ✓ Frontmatter valide
  ✓ Slugs uniques

Composants
  ✓ 12 composants résolus
  ⚠ custom-widget.html : HTML non standard (ligne 15)

Variables
  ✓ 23 variables résolues

Assets
  ✓ 8 fichiers référencés trouvés

Résultat : VALIDE (1 warning)
```
