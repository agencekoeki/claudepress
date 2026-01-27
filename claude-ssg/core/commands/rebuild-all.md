---
name: rebuild-all
description: Reconstruit tous les sites du projet
arguments:
  - name: --force
    required: false
    description: Force la régénération même si aucun changement détecté
---

# Commande : rebuild-all

## But
Reconstruire tous les sites du projet en une seule commande.

## Syntaxe
```
/rebuild-all
/rebuild-all --force
```

## Utilisation typique
Après une modification du thème ou du type de site qui affecte plusieurs sites.

## Étapes d'exécution

### ÉTAPE 1 : Inventaire
1. Lister tous les dossiers dans `/sites/` (sauf `_template`)
2. Afficher le nombre de sites à construire

### ÉTAPE 2 : Validation globale
1. Pour chaque site, exécuter `/validate` en mode silencieux
2. Si erreurs critiques : lister les sites problématiques
3. Demander confirmation pour continuer avec les sites valides

### ÉTAPE 3 : Construction
1. Pour chaque site valide, exécuter `/build`
2. Afficher la progression

### ÉTAPE 4 : Rapport
1. Afficher le résumé des builds
2. Lister les erreurs éventuelles

## Sortie
```
[REBUILD-ALL]

Sites détectés : 3
  - mon-blog
  - portfolio
  - docs

Validation...
  ✓ mon-blog : OK
  ✓ portfolio : OK
  ⚠ docs : 2 warnings

Construction...
  ✓ mon-blog : 5 pages (0.3s)
  ✓ portfolio : 8 pages (0.5s)
  ✓ docs : 23 pages (1.2s)

Terminé : 3 sites, 36 pages en 2.0s
```
