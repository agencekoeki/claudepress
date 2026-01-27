# Variables Engine

## Purpose

Manages variable definition, resolution, and substitution throughout the build process.

## Variable Syntax

```
{{namespace.path.to.value}}
```

## Namespaces

### `site`
Site-level configuration from `site.json`:
- `{{site.name}}` - Site name
- `{{site.url}}` - Site URL
- `{{site.language}}` - Language code

### `theme`
Theme design tokens from `design-system.md`:
- `{{theme.color.primary}}`
- `{{theme.font.family.base}}`
- `{{theme.spacing.md}}`

### `content`
Current page frontmatter:
- `{{content.title}}`
- `{{content.date}}`
- `{{content.author}}`

### `page`
Page metadata:
- `{{page.url}}` - Current page URL
- `{{page.path}}` - File path
- `{{page.slug}}` - URL slug

### `component`
Component-specific:
- `{{component.slot}}` - Slot content
- `{{component.props.*}}` - Passed properties

## Resolution Order

1. Component scope (props, slots)
2. Content scope (frontmatter)
3. Page scope (metadata)
4. Site scope (configuration)
5. Theme scope (design tokens)

## Default Values

```
{{variable|default:"fallback value"}}
```

## Conditional

```
{{#if variable}}
  Content when true
{{/if}}
```

## Iteration

```
{{#each items}}
  {{this.property}}
{{/each}}
```

## Escaping

- `{{variable}}` - HTML escaped (safe)
- `{{{variable}}}` - Raw output (unsafe)
