# Command: list-site-types

## Purpose
List all available site types in the framework.

## Syntax
```
list-site-types [--details]
```

## Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| --details | No | Show extended information |

## Execution Steps

### STEP 1: Scan Site-Types Directory
Read all directories in `site-types/` except `_template`

### STEP 2: Load Metadata
For each type, read `preset.json`

### STEP 3: Display List

## Output

### Basic List
```
Available Site Types
====================

1. landing
2. blog
3. portfolio
4. documentation

Total: 4 site types
```

### Detailed List (--details)
```
Available Site Types
====================

landing
  Description:  Single-page landing sites
  Default pages: index
  Components:   hero, cta, features

blog
  Description:  Blog with posts and categories
  Default pages: index, blog
  Components:   post-list, post-card, pagination

portfolio
  Description:  Portfolio showcase
  Default pages: index, projects
  Components:   project-grid, project-card

documentation
  Description:  Documentation sites
  Default pages: index, docs
  Components:   sidebar, toc, code-highlight

Total: 4 site types
```

## Related Commands
- `new-site-type` - Create a new type
- `list-themes` - List themes
- `init-site` - Create site with type
