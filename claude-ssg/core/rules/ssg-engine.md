# SSG Engine Rules

## Core Principles

1. **Deterministic Output**: Same input always produces same output
2. **Component Isolation**: Components are self-contained units
3. **Cascade Override**: Site > Site-Type > Theme (most specific wins)
4. **Validation First**: Always validate before building

## Processing Pipeline

```
Content (Markdown)
    → Parser (extract structure)
    → Assembler (apply components)
    → Variables (substitute values)
    → Output (static HTML)
```

## Override Cascade

When resolving a component:

1. Check `sites/{site}/overrides/components/`
2. Check `site-types/{type}/components/`
3. Check `themes/{theme}/components/`
4. Use default if none found

## Variable Resolution

Variables use the `{{variable}}` syntax:

- `{{site.name}}` - Site-level variables
- `{{theme.color.primary}}` - Theme design tokens
- `{{content.title}}` - Content frontmatter
- `{{component.slot}}` - Component slots

## File Processing Rules

1. `.md` files in `content/` are processed as pages
2. Files starting with `_` are ignored in output
3. Assets are copied verbatim to `public/`
4. Component `.html` files are never output directly

## Error Handling

- Missing component: WARN and use fallback
- Missing variable: ERROR and stop build
- Invalid structure: ERROR with specific location
- Circular reference: ERROR and stop build
