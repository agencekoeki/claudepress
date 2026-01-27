---
name: init-site
description: Initialise un nouveau site avec un thème et un type de site
arguments:
  - name: nom
    required: true
    description: Nom du site à créer
  - name: --theme
    required: true
    description: Thème à utiliser
  - name: --type
    required: true
    description: Type de site à utiliser
---

# Commande : init-site

## But
Créer un nouveau site en combinant un thème et un type de site existants.

## Syntaxe
```
/init-site [nom] --theme=[theme] --type=[type]
```

## Exemple
```
/init-site mon-blog --theme=minimal --type=blog
```

## Pré-requis
- Le thème spécifié doit exister dans `/themes/`
- Le type de site spécifié doit exister dans `/site-types/`
- Aucun site avec ce nom ne doit exister

## Étapes d'exécution

### ÉTAPE 1 : Validation
1. Vérifier que le thème existe
2. Vérifier que le type de site existe
3. Vérifier qu'aucun site avec ce nom n'existe

### ÉTAPE 2 : Création
1. Copier la structure de `/sites/_template/`
2. Configurer `site.json` avec les paramètres fournis
3. Créer la page d'accueil par défaut

### ÉTAPE 3 : Confirmation
Afficher les prochaines étapes suggérées.

## Fichiers créés
```
sites/[nom]/
├── site.json
├── content/
│   └── index.md
├── overrides/
│   ├── components/
│   └── ux-tweaks.md
├── public/
└── _state/
    └── manifest.json
```
