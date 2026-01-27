# Site Structure

## Overview

This document defines the page structure and content organization rules for this site type.

## Page Hierarchy

```
/                   # Home page (index.md)
├── /about          # About page
├── /contact        # Contact page
└── /[pages]/       # Additional pages
```

## Required Pages

| Page | File | Description |
|------|------|-------------|
| Home | content/index.md | Landing page |

## Page Templates

### Default Template
Used for standard content pages.

**Sections:**
1. Header (from theme)
2. Page title (h1)
3. Content body
4. Footer (from theme)

**Frontmatter:**
```yaml
---
title: Page Title
description: Page description for SEO
template: default
---
```

## Content Rules

### Headings
- One H1 per page (page title)
- Logical hierarchy (H2 → H3 → H4)
- No skipping levels

### Images
- Always include alt text
- Use relative paths
- Optimize for web

### Links
- Internal: use relative paths
- External: open in new tab
- Always descriptive text

## URL Structure

| Content Path | Output URL |
|--------------|------------|
| content/index.md | / |
| content/about.md | /about/ |
| content/blog/post.md | /blog/post/ |

## SEO Requirements

### Meta Tags
- Title: `{page.title} - {site.name}`
- Description: from frontmatter or auto-generated
- Canonical URL

### Structured Data
- Organization (home page)
- Breadcrumbs (all pages)

## Performance Guidelines

- Lazy load images below fold
- Minimize critical CSS
- Defer non-essential scripts
