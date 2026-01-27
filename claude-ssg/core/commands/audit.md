# Command: audit

## Purpose
Perform a comprehensive audit of a site, including content quality, accessibility, and performance recommendations.

## Syntax
```
audit <site-name> [--type=<audit-type>]
```

## Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| site-name | Yes | Site to audit |
| --type | No | Specific audit: all, content, accessibility, performance |

## Audit Types

### Content Audit
- Word count per page
- Reading level analysis
- Missing metadata
- Broken links
- Orphaned pages
- Image alt text coverage

### Accessibility Audit
- Heading hierarchy
- Color contrast (from theme)
- ARIA labels
- Keyboard navigation
- Focus indicators

### Performance Audit
- Image sizes
- Asset count
- CSS complexity
- Component nesting depth

## Execution Steps

### STEP 1: Load Site
1. Load site configuration
2. Load all content files
3. Load theme and site-type

### STEP 2: Run Audits
Execute selected audit checks

### STEP 3: Generate Report

## Output
```
Site Audit: my-site
===================

Content Audit
-------------
✓ All pages have titles
✓ No broken internal links
⚠ 2 images missing alt text
  - content/about.md:15
  - content/blog/post-1.md:8
✓ No orphaned pages

Accessibility Audit
-------------------
✓ Heading hierarchy valid
✓ All links have text
⚠ Review color contrast in theme

Performance Audit
-----------------
✓ No oversized images
✓ Component depth < 5
⚠ Consider lazy loading for 8 images

Summary
-------
Passed: 8
Warnings: 3
Errors: 0

Grade: A-
```

## Related Commands
- `validate` - Quick validation
- `status` - Site status
- `build` - Build after fixes
