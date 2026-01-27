# Parser Engine

## Purpose

The parser extracts structured data from Markdown content files, identifying frontmatter, headings, and content blocks.

## Input

Markdown files with optional YAML frontmatter:

```markdown
---
title: Page Title
template: default
---

# Heading

Content here...
```

## Output

Structured representation:

```json
{
  "frontmatter": {
    "title": "Page Title",
    "template": "default"
  },
  "content": [
    {
      "type": "heading",
      "level": 1,
      "text": "Heading"
    },
    {
      "type": "paragraph",
      "text": "Content here..."
    }
  ]
}
```

## Parsing Rules

### Frontmatter
- Delimited by `---` at file start
- Parsed as YAML
- Optional but recommended

### Content Blocks

| Markdown | Type | Properties |
|----------|------|------------|
| `# Text` | heading | level, text |
| `Text` | paragraph | text |
| `- Item` | list | items[], ordered |
| `> Quote` | blockquote | text |
| `` `code` `` | code-inline | text |
| ``` ```` ``` ``` | code-block | text, language |
| `![](url)` | image | src, alt |
| `[text](url)` | link | text, href |
| `---` | divider | - |

## Special Syntax

### Component Invocation

```markdown
::component-name
  prop: value
  slot: |
    Slot content here
::
```

### Variable Reference

```markdown
{{variable.path}}
```
