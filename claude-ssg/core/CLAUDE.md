# Claude SSG - Instructions Principales

## Vue d'ensemble
Claude SSG est un framework de génération de sites statiques (Static Site Generator) piloté par Claude.
Ce fichier contient les instructions principales pour Claude lors de l'utilisation du framework.

## Architecture

Le framework est organisé en 4 zones principales :

### 1. `/core/` - Le moteur
- `rules/` : Règles de fonctionnement du SSG
- `engine/` : Logique de parsing, assemblage et validation
- `commands/` : Toutes les commandes disponibles

### 2. `/themes/` - Les thèmes visuels
- Chaque thème définit le design system et les composants HTML
- Un thème = une identité visuelle complète

### 3. `/site-types/` - Les types de sites
- Définissent la structure et l'UX d'un type de site (blog, portfolio, docs...)
- Peuvent surcharger les composants du thème

### 4. `/sites/` - Les sites générés
- Chaque site combine un thème + un type de site
- Contient le contenu et les surcharges spécifiques

## Commandes disponibles

Pour exécuter une commande, l'utilisateur doit écrire :
`/commande [arguments]`

Consulter `/core/commands/` pour la liste complète des commandes.

## Règles fondamentales

1. **Séparation des responsabilités** : Le thème gère le visuel, le site-type gère la structure
2. **Cascade de surcharge** : Site > Site-Type > Thème
3. **Validation obligatoire** : Toujours valider avant de générer
4. **Traçabilité** : Chaque génération met à jour le manifest

## Pour commencer

1. Créer un thème : `/new-theme [nom]`
2. Créer un type de site : `/new-site-type [nom]`
3. Initialiser un site : `/init-site [nom] --theme=[theme] --type=[type]`
4. Construire : `/build [site]`
