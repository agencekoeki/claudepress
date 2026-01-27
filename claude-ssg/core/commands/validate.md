# Command: validate

## Purpose
Validate a site, theme, or site-type against framework rules.

## Syntax
```
validate <target> [--strict] [--fix]
```

## Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| target | Yes | Site, theme, or site-type name |
| --strict | No | Treat warnings as errors |
| --fix | No | Auto-fix minor issues |

## Prerequisites
- Target must exist

## Execution Steps

### STEP 1: Identify Target Type
Determine if target is:
- Site: `sites/{target}/site.json` exists
- Theme: `themes/{target}/theme.json` exists
- Site-type: `site-types/{target}/preset.json` exists

### STEP 2: Load Validation Rules
Load rules from `engine/validation-rules.md`

### STEP 3: Execute Validation
Run all applicable checks:

**For Sites:**
- [ ] site.json valid
- [ ] Theme exists
- [ ] Site-type exists
- [ ] Required content files exist
- [ ] No broken internal links
- [ ] All referenced components exist

**For Themes:**
- [ ] theme.json valid
- [ ] design-system.md exists
- [ ] Required components present
- [ ] Component templates valid

**For Site-Types:**
- [ ] preset.json valid
- [ ] ux-system.md exists
- [ ] structure.md exists

### STEP 4: Report Results

## Output
```
Validating site 'my-site'...

✓ site.json valid
✓ Theme 'minimal' exists
✓ Site-type 'blog' exists
✓ Required files present
✗ ERROR: Broken link in content/about.md:15
⚠ WARN: Missing alt text for image in content/index.md:8

Results: 1 error, 1 warning

Fix errors before building.
```

## Exit Codes
- 0: All checks passed
- 1: Warnings only (unless --strict)
- 2: Errors found

## Related Commands
- `build` - Build after validation
- `audit` - Detailed site audit
