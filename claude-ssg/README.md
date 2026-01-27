# Claude SSG

A static site generator framework designed to be operated by AI assistants.

## Overview

Claude SSG is a component-based static site generator that uses a layered architecture:

- **Themes**: Define visual appearance (CSS, design tokens, HTML components)
- **Site Types**: Define site structure and UX patterns (blog, portfolio, landing, etc.)
- **Sites**: Individual projects combining a theme + site-type + custom content

## Directory Structure

```
claude-ssg/
├── core/                    # Framework documentation
│   ├── CLAUDE.md            # AI assistant guide
│   ├── rules/               # Core rules
│   ├── engine/              # Engine documentation
│   └── commands/            # Command definitions
├── themes/                  # Theme definitions
│   └── _template/           # Theme template
├── site-types/              # Site type presets
│   └── _template/           # Site type template
├── sites/                   # Individual sites
│   └── _template/           # Site template
└── README.md                # This file
```

## Getting Started

### 1. Create a Theme

```
Run: new-theme my-theme
```

This creates a new theme with all required components and design tokens.

### 2. Create a Site Type

```
Run: new-site-type blog
```

This creates a site type preset with UX patterns and structure rules.

### 3. Initialize a Site

```
Run: init-site my-site --theme=my-theme --type=blog
```

This creates a new site using your theme and site type.

### 4. Build the Site

```
Run: build my-site
```

This generates static HTML in the site's `public/` directory.

## Commands

| Command | Description |
|---------|-------------|
| `init-project` | Initialize the framework |
| `init-site` | Create a new site |
| `build` | Generate static output |
| `new-page` | Create a new content page |
| `new-component` | Add a theme component |
| `new-theme` | Create a new theme |
| `new-site-type` | Create a new site type |
| `validate` | Validate site/theme/type |
| `status` | Show framework status |
| `preview` | Preview built site |
| `export` | Export for deployment |

See `core/commands/` for full documentation.

## Core Concepts

### Component Cascade

Components are resolved in order (most specific wins):
1. Site overrides
2. Site-type components
3. Theme components

### Variable System

Variables use `{{namespace.path}}` syntax:
- `{{site.name}}` - Site configuration
- `{{theme.color.primary}}` - Design tokens
- `{{content.title}}` - Page frontmatter

### Content Processing

1. Markdown files are parsed (frontmatter + content)
2. Content blocks map to components
3. Variables are substituted
4. Final HTML is assembled

## For AI Assistants

Read `core/CLAUDE.md` for detailed guidance on:
- Executing commands
- File conventions
- Modification rules
- Validation requirements

## License

MIT
