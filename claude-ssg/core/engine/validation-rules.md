# Validation Rules

## Purpose

Define rules for validating sites, themes, and components before build.

## Site Validation

### Required Files
- [ ] `site.json` exists and is valid JSON
- [ ] `content/index.md` exists
- [ ] Referenced theme exists
- [ ] Referenced site-type exists

### site.json Schema
```json
{
  "name": "string (required)",
  "theme": "string (required)",
  "siteType": "string (required)",
  "url": "string (optional)",
  "language": "string (optional, default: en)"
}
```

## Theme Validation

### Required Files
- [ ] `theme.json` exists and is valid JSON
- [ ] `design-system.md` exists
- [ ] `components/_index.md` exists
- [ ] Core components present (see below)

### Required Components
- `page-wrapper.html`
- `header.html`
- `footer.html`
- `heading.html`
- `paragraph.html`

### theme.json Schema
```json
{
  "name": "string (required)",
  "version": "string (required)",
  "author": "string (optional)",
  "description": "string (optional)"
}
```

## Site Type Validation

### Required Files
- [ ] `preset.json` exists and is valid JSON
- [ ] `ux-system.md` exists
- [ ] `structure.md` exists

### preset.json Schema
```json
{
  "name": "string (required)",
  "description": "string (optional)",
  "requiredComponents": ["array of strings"],
  "defaultPages": ["array of strings"]
}
```

## Component Validation

### HTML Template Rules
- Must be valid HTML fragment
- Variables must use `{{}}` syntax
- Slots must use `{{slot}}` placeholder
- No inline `<script>` tags
- No inline `<style>` tags (use CSS files)

## Content Validation

### Markdown Rules
- Frontmatter must be valid YAML
- Required frontmatter: `title`
- No broken internal links
- Images must reference existing files

## Error Levels

| Level | Action |
|-------|--------|
| ERROR | Stop build, must fix |
| WARN | Continue, but report |
| INFO | Informational only |
