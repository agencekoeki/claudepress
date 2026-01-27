# Composants spécifiques - Template

## Vue d'ensemble
Ce dossier contient les composants spécifiques à ce type de site.
Ils surchargent les composants du thème si le même nom est utilisé.

## Composants disponibles

*Aucun composant spécifique pour le template de base.*

## Ajouter un composant

Pour ajouter un composant spécifique à ce type de site :

1. Créer le fichier `.html` dans ce dossier
2. Documenter son utilisation ici
3. Il sera automatiquement prioritaire sur le thème

## Exemple

```html
<!--
    Composant: mon-composant
    Description: Description du composant

    Paramètres:
    - {{param1}}: Description
-->
<div class="mon-composant">
    {{slot:content}}
</div>
```

## Bonnes pratiques

1. **Nommage** : Utiliser des noms descriptifs et uniques
2. **Documentation** : Toujours documenter les paramètres
3. **Accessibilité** : Inclure les attributs ARIA nécessaires
4. **Réutilisabilité** : Prévoir des paramètres pour la personnalisation
