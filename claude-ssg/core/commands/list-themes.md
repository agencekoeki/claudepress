# Command: list-themes

## Purpose
List all available themes in the framework.

## Syntax
```
list-themes [--details]
```

## Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| --details | No | Show extended information |

## Execution Steps

### STEP 1: Scan Themes Directory
Read all directories in `themes/` except `_template`

### STEP 2: Load Metadata
For each theme, read `theme.json`

### STEP 3: Display List

## Output

### Basic List
```
Available Themes
================

1. minimal
2. corporate
3. blog-starter

Total: 3 themes
```

### Detailed List (--details)
```
Available Themes
================

minimal (v1.0.0)
  Author:      Claude
  Description: A clean, minimal theme
  Components:  15

corporate (v2.1.0)
  Author:      Design Team
  Description: Professional business theme
  Components:  22

blog-starter (v1.2.0)
  Author:      Claude
  Description: Perfect for blogs
  Components:  18

Total: 3 themes
```

## Usage Notes

- Themes starting with `_` are templates, not actual themes
- Use `new-theme` to create a new theme
- Use `validate <theme>` to check theme integrity

## Related Commands
- `new-theme` - Create a new theme
- `list-site-types` - List site types
