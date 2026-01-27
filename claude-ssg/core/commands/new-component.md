---
name: new-component
description: Crée un nouveau composant HTML dans un thème
arguments:
  - name: theme
    required: true
    description: Nom du thème cible
  - name: nom
    required: true
    description: Nom du composant
---

# Commande : new-component

## But
Créer un nouveau composant HTML réutilisable dans un thème.

## Syntaxe
```
/new-component [theme] [nom]
```

## Exemple
```
/new-component minimal card
/new-component corporate testimonial
```

## Pré-requis
- Le thème doit exister
- Le composant ne doit pas déjà exister dans ce thème

## Étapes d'exécution

### ÉTAPE 1 : Validation
1. Vérifier que le thème existe
2. Vérifier que le composant n'existe pas

### ÉTAPE 2 : Création
1. Créer le fichier HTML avec la structure de base
2. Mettre à jour `_index.md` du thème

### ÉTAPE 3 : Documentation
1. Ajouter une entrée dans `components/_index.md`
2. Suggérer les paramètres communs

## Template du composant
```html
<!--
    Composant: [nom]
    Thème: [theme]

    Paramètres:
    - {{param1}}: Description
    - {{param2}}: Description
-->
<div class="[nom]">
    {{slot:content}}
</div>
```

## Fichier créé
```
themes/[theme]/components/[nom].html
```

## Bonnes pratiques
- Utiliser des classes CSS avec le nom du composant comme préfixe
- Documenter tous les paramètres en commentaire
- Prévoir des valeurs par défaut quand c'est pertinent
