---
name: override-component
description: Surcharge un composant pour un site spécifique
arguments:
  - name: site
    required: true
    description: Nom du site
  - name: composant
    required: true
    description: Nom du composant à surcharger
---

# Commande : override-component

## But
Créer une surcharge locale d'un composant pour un site spécifique.

## Syntaxe
```
/override-component [site] [composant]
```

## Exemple
```
/override-component mon-blog header
```

## Étapes d'exécution

### ÉTAPE 1 : Localisation
1. Trouver le composant dans la cascade (type de site → thème)
2. Si non trouvé : erreur

### ÉTAPE 2 : Copie
1. Copier le composant vers `sites/[site]/overrides/components/`
2. Ajouter un commentaire indiquant l'origine

### ÉTAPE 3 : Confirmation
1. Afficher le chemin du fichier créé
2. Rappeler que les modifications seront prioritaires

## Résultat
```
[OVERRIDE] header.html

Source: themes/minimal/components/header.html
Destination: sites/mon-blog/overrides/components/header.html

Le composant a été copié. Modifiez-le selon vos besoins.
Cette version sera utilisée à la place de l'originale pour ce site.
```

## Notes
- La surcharge est prioritaire sur le thème et le type de site
- Pour annuler : supprimer le fichier dans `overrides/components/`
- Utilisez `/diff` pour comparer avec l'original après modifications
