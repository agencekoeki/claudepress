# Claude SSG - Core Documentation

## Overview

Claude SSG is a static site generator framework designed to be operated by AI assistants. It uses a component-based architecture with themes, site-types, and per-site customization.

## Architecture

### Directory Structure

```
claude-ssg/
├── core/           # Framework core - rules, engine, commands
├── themes/         # Visual themes with design systems
├── site-types/     # Site type presets (blog, portfolio, etc.)
└── sites/          # Individual site projects
```

### Core Concepts

1. **Themes**: Define visual appearance (CSS, components, design tokens)
2. **Site Types**: Define site structure and UX patterns
3. **Sites**: Individual projects combining a theme + site-type + content

## For AI Assistants

### Command Execution

All commands are defined in `./commands/`. Execute them by:
1. Reading the command file
2. Following the steps exactly
3. Validating output against expected results

### File Conventions

- Use `.md` for documentation and configuration rules
- Use `.json` for structured data
- Use `.html` for component templates
- Maintain `.gitkeep` files in empty directories

### Modification Rules

1. Never modify files in `core/` without explicit request
2. Always validate changes against `engine/validation-rules.md`
3. Document all structural changes

## Quick Reference

| Command | Purpose |
|---------|---------|
| `init-project` | Create framework structure |
| `init-site` | Initialize a new site |
| `build` | Generate static output |
| `new-page` | Create a new page |
| `validate` | Check site integrity |

See `./commands/` for full command documentation.
