---
name: new-theme
description: Crée un nouveau thème à partir du template
arguments:
  - name: nom
    required: true
    description: Nom du thème à créer
---

# Commande : new-theme

## But
Créer un nouveau thème visuel complet à partir du template de base.

## Syntaxe
```
/new-theme [nom]
```

## Exemple
```
/new-theme minimal
/new-theme corporate-blue
```

## Pré-requis
- Aucun thème avec ce nom ne doit exister

## Étapes d'exécution

### ÉTAPE 1 : Validation
1. Vérifier que le nom est valide (a-z, 0-9, -)
2. Vérifier qu'aucun thème avec ce nom n'existe

### ÉTAPE 2 : Création
1. Copier `/themes/_template/` vers `/themes/[nom]/`
2. Mettre à jour `theme.json` avec le nom
3. Personnaliser `design-system.md`

### ÉTAPE 3 : Confirmation
Afficher les prochaines étapes pour personnaliser le thème.

## Structure créée
```
themes/[nom]/
├── theme.json
├── design-system.md
├── components/
│   ├── _index.md
│   └── [tous les composants de base]
└── assets/
    ├── css/
    ├── js/
    ├── fonts/
    └── images/
```

## Prochaines étapes suggérées
1. Éditer `design-system.md` pour définir vos couleurs, typographie, espacements
2. Personnaliser les composants HTML
3. Ajouter vos assets CSS/JS
4. Tester avec `/init-site test --theme=[nom] --type=_template`
