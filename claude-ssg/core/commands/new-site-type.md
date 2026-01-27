---
name: new-site-type
description: Crée un nouveau type de site à partir du template
arguments:
  - name: nom
    required: true
    description: Nom du type de site à créer
---

# Commande : new-site-type

## But
Créer un nouveau type de site (blog, portfolio, documentation, etc.).

## Syntaxe
```
/new-site-type [nom]
```

## Exemple
```
/new-site-type blog
/new-site-type portfolio
/new-site-type documentation
```

## Pré-requis
- Aucun type de site avec ce nom ne doit exister

## Étapes d'exécution

### ÉTAPE 1 : Validation
1. Vérifier que le nom est valide (a-z, 0-9, -)
2. Vérifier qu'aucun type avec ce nom n'existe

### ÉTAPE 2 : Création
1. Copier `/site-types/_template/` vers `/site-types/[nom]/`
2. Mettre à jour `preset.json` avec le nom
3. Personnaliser `ux-system.md` et `structure.md`

### ÉTAPE 3 : Confirmation
Afficher les prochaines étapes pour personnaliser le type de site.

## Structure créée
```
site-types/[nom]/
├── preset.json
├── ux-system.md
├── structure.md
├── components/
│   └── _index.md
└── content-templates/
    └── _index.md
```

## Prochaines étapes suggérées
1. Définir la structure des pages dans `structure.md`
2. Créer les templates de contenu spécifiques
3. Ajouter des composants spécialisés si nécessaire
4. Documenter l'UX dans `ux-system.md`
