# Command: new-component

## Purpose
Create a new component in a theme.

## Syntax
```
new-component <theme-name> <component-name>
```

## Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| theme-name | Yes | Target theme |
| component-name | Yes | Component name (kebab-case) |

## Prerequisites
- Theme must exist
- Component must not already exist in theme

## Execution Steps

### STEP 1: Validation
1. Verify theme exists
2. Verify component name is valid (kebab-case)
3. Verify component doesn't exist

### STEP 2: Create Component
Create `themes/{theme}/components/{component-name}.html`:

```html
<!-- Component: {component-name} -->
<div class="{component-name}">
  {{slot}}
</div>
```

### STEP 3: Update Index
Add entry to `themes/{theme}/components/_index.md`:

```markdown
## {component-name}

Description: [Add description]

Props:
- slot: Main content

Usage:
:::{component-name}
  Content here
:::
```

## Output
```
Component created: themes/<theme>/components/<component-name>.html

Next steps:
1. Edit the component template
2. Add styles in assets/css/
3. Update _index.md with documentation
```

## Component Template Guidelines

- Use semantic HTML
- Include `{{slot}}` for content
- Use BEM-style class naming
- Keep components focused and reusable
- Document all props in _index.md

## Related Commands
- `new-theme` - Create a new theme
- `override-component` - Override in site
