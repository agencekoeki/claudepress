# Index des Composants - Template

## Composants de structure

| Composant | Fichier | Description |
|-----------|---------|-------------|
| Page Wrapper | `page-wrapper.html` | Structure de base de la page |
| Header | `header.html` | En-tête du site |
| Footer | `footer.html` | Pied de page |
| Navigation | `nav.html` | Menu de navigation principal |
| Nav Item | `nav-item.html` | Élément de navigation |

## Composants de contenu

| Composant | Fichier | Description |
|-----------|---------|-------------|
| Article | `article.html` | Conteneur d'article complet |
| Article Card | `article-card.html` | Aperçu d'article en carte |
| Heading | `heading.html` | Titres H1-H6 |
| Paragraph | `paragraph.html` | Paragraphe de texte |
| Link | `link.html` | Lien hypertexte |
| Button | `button.html` | Bouton d'action |
| Image | `image.html` | Image avec légende optionnelle |
| List | `list.html` | Liste ordonnée ou non |
| List Item | `list-item.html` | Élément de liste |
| Blockquote | `blockquote.html` | Citation |
| Code Block | `code-block.html` | Bloc de code |
| Code Inline | `code-inline.html` | Code en ligne |
| Divider | `divider.html` | Séparateur horizontal |

## Utilisation

Chaque composant peut être inclus avec :
```
{{include:nom-composant param="valeur"}}
```

Ou automatiquement lors du parsing Markdown.
