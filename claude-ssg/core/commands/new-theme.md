# Command: new-theme

## Purpose
Create a new theme with all required files and structure.

## Syntax
```
new-theme <theme-name> [--from=<base-theme>]
```

## Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| theme-name | Yes | Theme identifier (kebab-case) |
| --from | No | Base theme to copy from |

## Prerequisites
- Theme name must not already exist
- Base theme must exist if specified

## Execution Steps

### STEP 1: Validation
1. Verify theme name is valid (kebab-case)
2. Verify theme doesn't exist
3. Verify base theme if specified

### STEP 2: Create Structure
Copy from `themes/_template/` to `themes/<theme-name>/`:

```
themes/<theme-name>/
├── theme.json
├── design-system.md
├── components/
│   ├── _index.md
│   └── [all base components]
└── assets/
    ├── css/
    ├── js/
    ├── fonts/
    └── images/
```

### STEP 3: Configure Theme
Update `theme.json`:
```json
{
  "name": "<theme-name>",
  "version": "1.0.0",
  "author": "",
  "description": "",
  "created": "<timestamp>"
}
```

### STEP 4: Initialize Design System
Create `design-system.md` with default tokens.

## Output
```
Theme '<theme-name>' created successfully!

Location: themes/<theme-name>/

Next steps:
1. Edit theme.json with metadata
2. Define design tokens in design-system.md
3. Customize components in components/
4. Add styles in assets/css/
```

## Related Commands
- `new-component` - Add component to theme
- `list-themes` - List available themes
