---
name: diff
description: Compare deux versions d'un composant ou fichier
arguments:
  - name: fichier1
    required: true
    description: Premier fichier (ou "original" pour le composant de base)
  - name: fichier2
    required: true
    description: Second fichier (ou "override" pour la surcharge)
---

# Commande : diff

## But
Comparer deux fichiers pour voir les différences.

## Syntaxe
```
/diff [fichier1] [fichier2]
/diff original override --site=[site] --component=[nom]
```

## Exemples
```
/diff themes/minimal/components/header.html themes/corporate/components/header.html
/diff original override --site=mon-blog --component=header
```

## Sortie
```
[DIFF] header.html

Original: themes/minimal/components/header.html
Override: sites/mon-blog/overrides/components/header.html

@@ -1,5 +1,7 @@
 <header class="site-header">
-    <div class="logo">{{site.name}}</div>
+    <div class="logo">
+        <img src="{{site.logo}}" alt="{{site.name}}">
+    </div>
     <nav>
         {{include:nav}}
     </nav>

Résumé:
  - 2 lignes ajoutées
  - 1 ligne supprimée
  - 1 ligne modifiée
```

## Utilisation
Cette commande est utile pour :
- Voir les modifications apportées à une surcharge
- Comparer deux thèmes
- Vérifier les changements avant un commit
- Documenter les personnalisations

## Format de sortie
Le diff utilise le format unifié (comme git diff) :
- Lignes commençant par `-` : supprimées
- Lignes commençant par `+` : ajoutées
- Lignes sans préfixe : contexte (non modifiées)
