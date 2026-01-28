# Claude SSG

Générateur de site statique piloté par Claude Code.

## Structure
```
claude-ssg/
├── core/           ← Moteur (ne pas modifier)
├── themes/         ← Thèmes visuels
├── site-types/     ← Types de sites (UX)
└── sites/          ← Vos sites
```

## Commandes

| Commande | Description |
|----------|-------------|
| `/project:init-site` | Créer un nouveau site |
| `/project:build` | Builder le site |
| `/project:new-page` | Ajouter une page |
| `/project:validate` | Valider le site |
| `/project:status` | État du site |

## Documentation

- `core/CLAUDE.md` — Instructions système
- `core/engine/*.md` — Spécifications techniques
- `themes/_template/design-system.md` — Template design system
- `site-types/_template/ux-system.md` — Template règles UX

## Licence

MIT
