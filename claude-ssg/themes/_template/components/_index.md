# Index des composants du thème

Ce dossier contient les templates HTML des composants.

## Composants obligatoires
- `header.html` — Header du site
- `footer.html` — Footer du site
- `nav.html` — Navigation principale
- `nav-item.html` — Item de navigation (utilisé dans nav.html)
- `page-wrapper.html` — Template de base HTML

## Composants de contenu
- `article.html` — Article/page complète
- `article-card.html` — Carte d'article (pour listings)

## Composants typographiques
Ces composants sont utilisés lors du parsing Markdown :
- `heading.html` — Titres (h1-h6)
- `paragraph.html` — Paragraphes
- `link.html` — Liens
- `button.html` — Boutons
- `image.html` — Images
- `list.html` — Listes (ul, ol)
- `list-item.html` — Item de liste
- `blockquote.html` — Citations
- `code-block.html` — Blocs de code
- `code-inline.html` — Code inline
- `divider.html` — Séparateurs (hr)

## Règles
1. Chaque composant utilise UNIQUEMENT les classes `th-*`
2. Chaque composant est autonome (pas de dépendance cachée)
3. Les variables `{{...}}` sont documentées dans le fichier
4. Les composants sont versionnés avec le thème
