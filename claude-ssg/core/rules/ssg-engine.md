---
name: ssg-engine
description: Règles automatiquement chargées pour le fonctionnement du SSG
alwaysApply: true
---

# Règles SSG Engine

## Règle 1 : Contexte obligatoire
Avant TOUTE opération de build, tu DOIS charger :
- Le `site.json` du site actif
- Le `theme.json` du thème utilisé
- Le `preset.json` du site-type utilisé
- Le `design-system.md` du thème
- Le `ux-system.md` du site-type

## Règle 2 : Format HTML
- Doctype : `<!DOCTYPE html>`
- Lang : attribut `lang` obligatoire sur `<html>`
- Charset : `<meta charset="UTF-8">` en premier dans `<head>`
- Viewport : `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
- Indentation : 2 espaces
- Pas de lignes vides multiples
- Attributs HTML : guillemets doubles uniquement

## Règle 3 : Classes CSS
- Format : kebab-case uniquement (`main-header`, pas `mainHeader`)
- Préfixes :
  - `th-` : classes du thème
  - `st-` : classes du site-type
  - `c-` : classes custom/override
- JAMAIS de classes sans préfixe (sauf classes utilitaires Tailwind si utilisé)

## Règle 4 : Variables
- Syntaxe : `{{variable}}` ou `{{object.property}}`
- Échappement HTML : automatique sauf `{{{raw}}}`
- Variables non résolues : ERREUR (ne pas laisser `{{xxx}}` dans l'output)

## Règle 5 : Fichiers
- Encodage : UTF-8 sans BOM
- Fins de ligne : LF (pas CRLF)
- Noms de fichiers : kebab-case, pas d'espaces, pas de caractères spéciaux
- Extensions : `.html` pour les pages, `.md` pour le contenu

## Règle 6 : Structure des URLs
- Mode : "pretty URLs" par défaut
- `content/about.md` → `public/about/index.html`
- `content/blog/mon-article.md` → `public/blog/mon-article/index.html`
- `content/index.md` → `public/index.html` (exception)

## Règle 7 : Assets
- Chemin : toujours relatif à la racine (`/assets/css/style.css`)
- Pas de CDN externe sauf autorisation explicite dans `site.json`
- Images : attribut `alt` OBLIGATOIRE

## Règle 8 : Manifest
Après chaque build, mettre à jour `_state/manifest.json` :
```json
{
  "lastBuild": "ISO-8601",
  "generator": "claude-ssg",
  "version": "1.0.0",
  "site": "nom-du-site",
  "theme": "nom-du-theme",
  "siteType": "nom-du-type",
  "files": {
    "source-path": {
      "hash": "sha256-du-contenu-source",
      "output": "chemin-output",
      "buildTime": "ISO-8601"
    }
  }
}
```

## Règle 9 : Gestion des erreurs
- Fichier source manquant : ERREUR BLOQUANTE
- Composant manquant : ERREUR BLOQUANTE
- Variable non résolue : ERREUR BLOQUANTE
- Spec incohérente : AVERTISSEMENT + demande de clarification

## Règle 10 : Communication
- Toujours confirmer ce qui va être fait AVANT de le faire
- Lister les fichiers qui seront créés/modifiés
- Résumer les actions effectuées APRÈS
- En cas d'erreur : expliquer clairement + proposer une solution
