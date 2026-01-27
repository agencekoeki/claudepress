# Parser - Moteur de parsing Markdown

## Rôle
Convertir le contenu Markdown en structure de données exploitable.

## Entrée
Fichier `.md` avec frontmatter YAML optionnel.

## Sortie
Objet structuré contenant :
- `metadata` : Données du frontmatter
- `content` : Contenu parsé en blocs
- `references` : Liens, images, composants référencés

## Format du frontmatter

```yaml
---
title: "Titre de la page"
slug: "mon-slug"
template: "default"
date: "2024-01-15"
tags: ["tag1", "tag2"]
custom_field: "valeur"
---
```

## Blocs reconnus

| Type | Syntaxe Markdown | Composant HTML |
|------|------------------|----------------|
| Titre H1 | `# Texte` | `heading.html` (level=1) |
| Titre H2-H6 | `## à ######` | `heading.html` (level=2-6) |
| Paragraphe | Texte simple | `paragraph.html` |
| Liste | `- item` ou `1. item` | `list.html` + `list-item.html` |
| Lien | `[texte](url)` | `link.html` |
| Image | `![alt](src)` | `image.html` |
| Code inline | `` `code` `` | `code-inline.html` |
| Code block | ``` ``` lang ``` ``` | `code-block.html` |
| Citation | `> texte` | `blockquote.html` |
| Séparateur | `---` | `divider.html` |

## Composants personnalisés

Syntaxe pour insérer un composant :
```
{{component:nom param1="valeur1" param2="valeur2"}}
```

Exemple :
```
{{component:button text="Cliquez ici" href="/contact" variant="primary"}}
```

## Règles de parsing

1. Le frontmatter est toujours en premier (optionnel)
2. Les lignes vides séparent les blocs
3. Les composants personnalisés sont sur une ligne seule
4. Le HTML brut est préservé tel quel
