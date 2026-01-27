# CLAUDE.md - AI Assistant Guide for claudepress

This document provides guidance for AI assistants working on the claudepress repository.

## Project Overview

**claudepress** contains the Claude SSG framework - a static site generator designed to be operated by AI assistants. It uses a component-based architecture with themes, site-types, and per-site customization.

### Current State

- **Status**: Framework initialized
- **Content**: Complete Claude SSG framework structure
- **Dependencies**: None (documentation-driven framework)
- **Build System**: AI-operated via command documentation

## Repository Structure

```
claudepress/
├── CLAUDE.md                    # This file - AI assistant guidance
├── readme.md                    # Project readme
└── claude-ssg/                  # Main framework directory
    ├── core/                    # Framework internals
    │   ├── CLAUDE.md            # Framework-specific AI guide
    │   ├── rules/               # Core engine rules
    │   │   └── ssg-engine.md
    │   ├── engine/              # Engine documentation
    │   │   ├── parser.md
    │   │   ├── assembler.md
    │   │   ├── variables.md
    │   │   ├── file-structure.md
    │   │   └── validation-rules.md
    │   └── commands/            # Command definitions (18 commands)
    │       ├── init-project.md
    │       ├── init-site.md
    │       ├── build.md
    │       └── ... (15 more)
    ├── themes/                  # Theme definitions
    │   └── _template/           # Base theme template
    │       ├── theme.json
    │       ├── design-system.md
    │       ├── components/      # 18 HTML components
    │       └── assets/          # CSS, JS, fonts, images
    ├── site-types/              # Site type presets
    │   └── _template/           # Base site-type template
    │       ├── preset.json
    │       ├── ux-system.md
    │       ├── structure.md
    │       ├── components/
    │       └── content-templates/
    ├── sites/                   # Individual site projects
    │   └── _template/           # Base site template
    │       ├── site.json
    │       ├── content/
    │       ├── overrides/
    │       ├── public/
    │       └── _state/
    └── README.md                # Framework documentation
```

## Development Guidelines

### Git Workflow

1. **Branch Naming**: Feature branches follow `claude/<feature-name>-<session-id>`
2. **Commits**: Write clear, descriptive commit messages
3. **Main Branch**: Protected - all changes through feature branches
4. **Push Commands**: Always use `git push -u origin <branch-name>`

### Framework Conventions

- **Documentation Files**: Use `.md` for rules, guides, and configuration
- **Data Files**: Use `.json` for structured configuration
- **Component Files**: Use `.html` for component templates
- **Placeholders**: Use `.gitkeep` for empty directories
- **Templates**: Directories named `_template/` are base templates, not actual content

### Component Cascade

When resolving components, the framework uses this priority:
1. `sites/{site}/overrides/components/` (highest priority)
2. `site-types/{type}/components/`
3. `themes/{theme}/components/` (lowest priority)

### Variable Syntax

Variables use `{{namespace.path}}` format:
- `{{site.name}}` - Site configuration
- `{{theme.color.primary}}` - Design tokens
- `{{content.title}}` - Page frontmatter
- `{{slot}}` - Component slot content

## For AI Assistants

### Executing Commands

All commands are defined in `claude-ssg/core/commands/`. To execute:
1. Read the command file
2. Follow the steps exactly as documented
3. Validate output against expected results
4. Handle errors according to documented behavior

### Before Making Changes

1. **Read First**: Always read files before modifying them
2. **Understand Context**: Explore related files to understand patterns
3. **Check Cascade**: Understand where components/styles come from
4. **Validate**: Run validation before and after changes

### Key Rules

1. **Never modify `core/`** without explicit request
2. **Respect the cascade** - site overrides type overrides theme
3. **Use templates** - copy from `_template/` directories for new items
4. **Document changes** - update relevant `.md` files
5. **Validate everything** - use the `validate` command

### File Operations

- Prefer editing existing files over creating new ones
- Copy from `_template/` when creating new themes/sites/types
- Maintain `.gitkeep` files in empty directories
- Never output component `.html` files directly to public

## Quick Reference

### Common Commands

| Command | Purpose |
|---------|---------|
| `init-site <name>` | Create a new site |
| `build <site>` | Generate static output |
| `new-page <site> <path>` | Create content page |
| `new-theme <name>` | Create new theme |
| `new-site-type <name>` | Create site type |
| `validate <target>` | Validate configuration |
| `status [site]` | Show current status |
| `preview <site>` | Local preview server |

### Important Files

| File | Purpose |
|------|---------|
| `CLAUDE.md` | AI assistant guidance (this file) |
| `claude-ssg/core/CLAUDE.md` | Framework-specific AI guide |
| `claude-ssg/README.md` | Framework documentation |
| `claude-ssg/core/rules/ssg-engine.md` | Core engine rules |
| `claude-ssg/core/engine/validation-rules.md` | Validation rules |

### Key Resources

- Framework docs: `claude-ssg/README.md`
- Engine rules: `claude-ssg/core/rules/ssg-engine.md`
- All commands: `claude-ssg/core/commands/`
- Validation: `claude-ssg/core/engine/validation-rules.md`

---

**Last Updated**: 2026-01-27
**Repository**: claudepress
**Status**: Claude SSG Framework Initialized
