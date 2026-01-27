# Templates de contenu - Template

## Vue d'ensemble
Ce dossier contient les templates de contenu Markdown.
Utilisés par la commande `/new-page` avec l'option `--template`.

## Templates disponibles

*Aucun template spécifique pour le template de base.*

## Structure d'un template

Un template de contenu est un fichier `.md` avec :
1. Un frontmatter pré-rempli
2. Une structure de contenu suggérée
3. Des placeholders à remplacer

## Exemple de template

```markdown
---
title: "{{TITLE}}"
slug: "{{SLUG}}"
date: "{{DATE}}"
template: "default"
---

# {{TITLE}}

## Introduction

[Écrivez votre introduction ici...]

## Contenu principal

[Développez votre contenu...]

## Conclusion

[Résumez les points clés...]
```

## Placeholders disponibles

| Placeholder | Remplacé par |
|-------------|--------------|
| `{{TITLE}}` | Titre fourni à la commande |
| `{{SLUG}}` | Slug généré |
| `{{DATE}}` | Date du jour |
| `{{AUTHOR}}` | Auteur du site (si défini) |

## Ajouter un template

1. Créer le fichier `.md` dans ce dossier
2. Utiliser les placeholders pour les valeurs dynamiques
3. Le template sera disponible via `/new-page --template=[nom]`
