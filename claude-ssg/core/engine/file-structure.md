# File Structure Specification

## Framework Root

```
claude-ssg/
├── core/                    # Framework internals (read-only)
├── themes/                  # Theme definitions
├── site-types/              # Site type presets
├── sites/                   # Individual sites
└── README.md                # Framework documentation
```

## Theme Structure

```
themes/{theme-name}/
├── theme.json               # Theme metadata
├── design-system.md         # Design tokens & rules
├── components/
│   ├── _index.md            # Component documentation
│   └── {component}.html     # Component templates
└── assets/
    ├── css/                 # Stylesheets
    ├── js/                  # Scripts
    ├── fonts/               # Web fonts
    └── images/              # Theme images
```

## Site Type Structure

```
site-types/{type-name}/
├── preset.json              # Type configuration
├── ux-system.md             # UX patterns & behavior
├── structure.md             # Page structure rules
├── components/
│   └── {component}.html     # Type-specific components
└── content-templates/
    └── {template}.md        # Content scaffolds
```

## Site Structure

```
sites/{site-name}/
├── site.json                # Site configuration
├── content/
│   └── {page}.md            # Content files
├── overrides/
│   ├── components/          # Component overrides
│   └── ux-tweaks.md         # UX modifications
├── public/                  # Static assets
└── _state/
    └── manifest.json        # Build state
```

## File Naming Conventions

| Pattern | Meaning |
|---------|---------|
| `_filename` | Internal/ignored in output |
| `.gitkeep` | Placeholder for empty dirs |
| `*.html` | Component template |
| `*.md` | Documentation or content |
| `*.json` | Configuration data |

## Reserved Names

- `_template/` - Template directories (not actual content)
- `_index.md` - Directory documentation
- `_state/` - Build state (auto-generated)
