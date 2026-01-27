---
name: export
description: Exporte un site pour déploiement
arguments:
  - name: site
    required: true
    description: Nom du site à exporter
  - name: --format
    required: false
    description: "Format d'export: zip, folder (défaut: folder)"
  - name: --dest
    required: false
    description: Destination de l'export
---

# Commande : export

## But
Préparer un site pour le déploiement en production.

## Syntaxe
```
/export [site]
/export [site] --format=zip
/export [site] --dest=/path/to/deploy
```

## Étapes d'exécution

### ÉTAPE 1 : Build
1. Exécuter `/build [site]` si nécessaire
2. Vérifier que le build est à jour

### ÉTAPE 2 : Optimisation
1. Minifier les fichiers HTML (optionnel)
2. Optimiser les assets
3. Générer les fichiers de production

### ÉTAPE 3 : Export
1. Copier le contenu de `public/` vers la destination
2. Si format=zip : créer une archive

## Fichiers exportés
```
export/[site]/
├── index.html
├── about.html
├── contact.html
├── assets/
│   ├── css/
│   ├── js/
│   ├── fonts/
│   └── images/
├── sitemap.xml (si configuré)
└── robots.txt (si configuré)
```

## Sortie
```
[EXPORT] mon-blog

Build vérifié : à jour
Optimisation...
  - HTML minifié : -15%
  - CSS combiné : 3 → 1 fichier

Export créé :
  Destination: ./export/mon-blog/
  Taille totale: 1.2 MB
  Fichiers: 23

Prêt pour déploiement !
```

## Déploiement suggéré
Le dossier exporté peut être déployé sur :
- Netlify (drag & drop)
- Vercel
- GitHub Pages
- Tout hébergement statique
