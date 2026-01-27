# Command: override-ux

## Purpose
Create or modify site-specific UX behavior overrides.

## Syntax
```
override-ux <site-name> [--edit]
```

## Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| site-name | Yes | Target site |
| --edit | No | Open existing ux-tweaks.md for editing |

## Prerequisites
- Site must exist

## Execution Steps

### STEP 1: Check Existing
Check if `sites/{site}/overrides/ux-tweaks.md` exists

### STEP 2: Create or Open
If doesn't exist, create with template:

```markdown
# UX Tweaks for {site-name}

## Overview
Document any UX behavior modifications for this site.

## Navigation
<!-- Describe navigation changes -->

## Interactions
<!-- Describe interaction changes -->

## Layout
<!-- Describe layout modifications -->

## Animations
<!-- Describe animation preferences -->

## Accessibility
<!-- Describe accessibility requirements -->
```

### STEP 3: Display Instructions

## Output
```
UX tweaks file ready!

Location: sites/my-site/overrides/ux-tweaks.md

This file documents UX behavior that differs from the site-type defaults.
Edit this file to specify custom behavior.

Reference:
- Site-type UX: site-types/blog/ux-system.md
```

## UX Override Examples

### Navigation Override
```markdown
## Navigation
- Mobile menu: slide-in from left (instead of dropdown)
- Sticky header: disabled on blog posts
```

### Interaction Override
```markdown
## Interactions
- Form submissions: show inline validation
- Links: no underline on hover
```

## Related Commands
- `override-component` - Override visual components
- `validate` - Validate UX configuration
