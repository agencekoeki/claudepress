# Command: status

## Purpose
Display the current status of a site or the entire framework.

## Syntax
```
status [<site-name>]
```

## Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| site-name | No | Specific site (omit for framework status) |

## Execution Steps

### Framework Status (no site specified)

1. Count themes in `themes/`
2. Count site-types in `site-types/`
3. Count sites in `sites/`
4. Check for issues

### Site Status (site specified)

1. Load `site.json`
2. Load `_state/manifest.json`
3. Check for changes since last build
4. Count content files
5. Check validation status

## Output

### Framework Status
```
Claude SSG Framework Status
===========================

Themes:        3 (minimal, corporate, blog)
Site Types:    2 (landing, blog)
Sites:         2 (my-site, company-site)

Framework:     OK
Last checked:  2024-01-15 10:30:00
```

### Site Status
```
Site Status: my-site
====================

Theme:         minimal
Site Type:     blog
Last Build:    2024-01-15 09:00:00

Content:
  Total pages: 5
  Modified:    2 (since last build)
  New:         1

State:         NEEDS REBUILD
Validation:    1 warning

Run 'build my-site' to update.
```

## Related Commands
- `validate` - Detailed validation
- `build` - Build site
- `audit` - Full site audit
