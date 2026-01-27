# Claude SSG

Un framework de génération de sites statiques (Static Site Generator) piloté par Claude.

## Vue d'ensemble

Claude SSG est un système modulaire qui permet de créer des sites statiques en combinant :
- **Thèmes** : Design system et composants visuels
- **Types de sites** : Structure et UX (blog, portfolio, docs...)
- **Sites** : Contenu et personnalisations

## Structure du projet

```
claude-ssg/
├── core/               # Moteur du SSG
│   ├── CLAUDE.md       # Instructions principales
│   ├── rules/          # Règles de fonctionnement
│   ├── engine/         # Logique de génération
│   └── commands/       # Commandes disponibles
├── themes/             # Thèmes visuels
├── site-types/         # Types de sites
├── sites/              # Sites générés
└── README.md           # Ce fichier
```

## Commandes disponibles

| Commande | Description |
|----------|-------------|
| `/init-project` | Initialiser le framework (fait) |
| `/new-theme [nom]` | Créer un nouveau thème |
| `/new-site-type [nom]` | Créer un nouveau type de site |
| `/init-site [nom]` | Créer un nouveau site |
| `/build [site]` | Générer les fichiers HTML |
| `/validate [site]` | Vérifier la configuration |
| `/status` | Voir l'état du projet |
| `/new-page [site] "[titre]"` | Créer une nouvelle page |

## Guide de démarrage

### 1. Créer un thème
```
/new-theme minimal
```
Personnalisez ensuite les couleurs, la typographie et les composants.

### 2. Créer un type de site
```
/new-site-type blog
```
Définissez la structure et les comportements UX.

### 3. Initialiser un site
```
/init-site mon-blog --theme=minimal --type=blog
```

### 4. Ajouter du contenu
```
/new-page mon-blog "Mon premier article"
```

### 5. Construire
```
/build mon-blog
```

## Architecture

### Cascade de composants
Les composants sont résolus dans cet ordre (priorité décroissante) :
1. Surcharges du site (`sites/[site]/overrides/components/`)
2. Composants du type de site (`site-types/[type]/components/`)
3. Composants du thème (`themes/[theme]/components/`)

### Variables
Trois niveaux de variables :
- `{{site.*}}` : Configuration du site
- `{{page.*}}` : Métadonnées de la page
- `{{theme.*}}` : Paramètres du thème

## Documentation

Consultez les fichiers dans `/core/` pour la documentation complète :
- `core/CLAUDE.md` : Instructions principales
- `core/rules/` : Règles du moteur
- `core/engine/` : Logique détaillée
- `core/commands/` : Documentation des commandes

## Licence

MIT
