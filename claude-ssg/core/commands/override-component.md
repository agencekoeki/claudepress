# Command: override-component

## Purpose
Create a site-specific override for a theme component.

## Syntax
```
override-component <site-name> <component-name>
```

## Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| site-name | Yes | Target site |
| component-name | Yes | Component to override |

## Prerequisites
- Site must exist
- Component must exist in theme or site-type

## Execution Steps

### STEP 1: Validation
1. Verify site exists
2. Find component in cascade (theme or site-type)
3. Verify override doesn't already exist

### STEP 2: Copy Component
1. Locate original component
2. Copy to `sites/{site}/overrides/components/{component}.html`

### STEP 3: Document Override
Update `sites/{site}/overrides/components/_index.md` (create if needed):

```markdown
## Overridden Components

### {component-name}
- Original: themes/{theme}/components/{component}.html
- Override: overrides/components/{component}.html
- Reason: [Add reason for override]
```

## Output
```
Component override created!

Original: themes/minimal/components/header.html
Override: sites/my-site/overrides/components/header.html

The site will now use your override instead of the theme component.

Next steps:
1. Edit the override file
2. Run 'build my-site' to see changes
```

## Override Cascade Reminder

Components are resolved in this order:
1. `sites/{site}/overrides/components/` ← Your override
2. `site-types/{type}/components/`
3. `themes/{theme}/components/`

## Related Commands
- `override-ux` - Override UX behavior
- `diff` - Compare override with original
