# File Structure - Conventions de fichiers

## Conventions de nommage

### Fichiers
- Tout en minuscules
- Mots séparés par des tirets : `mon-composant.html`
- Extensions appropriées : `.md`, `.html`, `.json`, `.css`, `.js`

### Dossiers
- Tout en minuscules
- Mots séparés par des tirets : `mon-dossier/`
- Préfixe `_` pour les dossiers système : `_state/`, `_template/`

### Slugs de pages
- Générés automatiquement depuis le titre si non spécifié
- Format : `mon-titre-de-page`
- Caractères autorisés : `a-z`, `0-9`, `-`

## Structure d'un thème

```
themes/[nom-theme]/
├── theme.json           # Configuration du thème
├── design-system.md     # Documentation du design system
├── components/          # Composants HTML
│   ├── _index.md        # Index des composants
│   └── *.html           # Fichiers de composants
└── assets/              # Ressources statiques
    ├── css/
    ├── js/
    ├── fonts/
    └── images/
```

## Structure d'un type de site

```
site-types/[nom-type]/
├── preset.json          # Configuration par défaut
├── ux-system.md         # Documentation UX
├── structure.md         # Structure des pages
├── components/          # Composants spécifiques
│   └── _index.md
└── content-templates/   # Templates de contenu
    └── _index.md
```

## Structure d'un site

```
sites/[nom-site]/
├── site.json            # Configuration du site
├── content/             # Contenu Markdown
│   ├── index.md
│   └── [pages].md
├── overrides/           # Surcharges
│   ├── components/
│   └── ux-tweaks.md
├── public/              # Fichiers générés (output)
│   └── *.html
└── _state/              # État interne
    └── manifest.json
```

## Fichiers spéciaux

| Fichier | Rôle |
|---------|------|
| `_index.md` | Documentation/index d'un dossier |
| `.gitkeep` | Préserve un dossier vide dans Git |
| `manifest.json` | État de la dernière génération |
| `*.json` | Configuration (toujours JSON valide) |
