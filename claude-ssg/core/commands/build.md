---
name: build
description: Génère les fichiers HTML d'un site
arguments:
  - name: site
    required: true
    description: Nom du site à construire
  - name: --force
    required: false
    description: Force la régénération complète (ignore le cache)
---

# Commande : build

## But
Générer tous les fichiers HTML d'un site à partir de son contenu Markdown.

## Syntaxe
```
/build [site]
/build [site] --force
```

## Exemple
```
/build mon-blog
/build mon-blog --force
```

## Pré-requis
- Le site doit exister dans `/sites/`
- Le thème référencé doit exister
- Le type de site référencé doit exister
- La validation doit passer (sinon erreur)

## Étapes d'exécution

### ÉTAPE 1 : Validation
1. Exécuter `/validate [site]` en mode silencieux
2. Si erreurs : afficher et STOPPER
3. Si warnings : afficher et continuer

### ÉTAPE 2 : Chargement
1. Charger `site.json`
2. Charger le thème référencé
3. Charger le type de site référencé
4. Construire la cascade de composants

### ÉTAPE 3 : Génération
Pour chaque fichier dans `content/` :
1. Parser le Markdown (voir `engine/parser.md`)
2. Assembler le HTML (voir `engine/assembler.md`)
3. Écrire dans `public/`

### ÉTAPE 4 : Assets
1. Copier les assets du thème vers `public/assets/`
2. Copier les assets spécifiques du site si existants

### ÉTAPE 5 : Manifest
1. Mettre à jour `_state/manifest.json`
2. Enregistrer les hashes des fichiers sources
3. Noter la date de génération

## Sortie
```
[BUILD] mon-blog
  ✓ index.md → index.html
  ✓ about.md → about.html
  ✓ contact.md → contact.html
  ✓ Assets copiés (12 fichiers)

Build terminé : 3 pages générées en 0.8s
```
