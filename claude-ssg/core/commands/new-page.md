# Command: new-page

## Purpose
Create a new content page in a site.

## Syntax
```
new-page <site-name> <page-path> [--template=<template>]
```

## Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| site-name | Yes | Target site |
| page-path | Yes | Page path (e.g., "about" or "blog/first-post") |
| --template | No | Content template to use |

## Prerequisites
- Site must exist
- Page must not already exist
- Template must exist if specified

## Execution Steps

### STEP 1: Validation
1. Verify site exists
2. Verify page path is valid
3. Verify page doesn't exist
4. Verify template if specified

### STEP 2: Resolve Template
If template specified:
- Use `site-types/{type}/content-templates/{template}.md`

If no template:
- Use default page template

### STEP 3: Create Page
Create `sites/{site}/content/{page-path}.md`:

```markdown
---
title: Page Title
template: default
created: <timestamp>
---

# Page Title

Content goes here...
```

### STEP 4: Create Directory
If page-path contains directories, create them.

## Output
```
Page created: sites/<site-name>/content/<page-path>.md

Next steps:
1. Edit the page content
2. Run 'build <site-name>' to generate output
```

## Examples

```bash
# Simple page
new-page my-site about

# Nested page
new-page my-site blog/my-first-post

# With template
new-page my-site blog/review --template=blog-post
```

## Related Commands
- `build` - Build site with new page
- `validate` - Validate page content
