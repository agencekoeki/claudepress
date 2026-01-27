# Assembler Engine

## Purpose

The assembler combines parsed content with component templates to produce final HTML output.

## Process

1. Load parsed content structure
2. Resolve template/layout
3. For each content block:
   - Find matching component
   - Apply component template
   - Substitute variables
4. Assemble final page

## Component Resolution

Components are resolved in cascade order:

```
1. sites/{site}/overrides/components/{name}.html
2. site-types/{type}/components/{name}.html
3. themes/{theme}/components/{name}.html
```

First match wins.

## Template Application

Given content block:
```json
{
  "type": "heading",
  "level": 2,
  "text": "Hello World"
}
```

And component `heading.html`:
```html
<h{{level}} class="heading heading--{{level}}">{{text}}</h{{level}}>
```

Output:
```html
<h2 class="heading heading--2">Hello World</h2>
```

## Slot Handling

Components can define slots for nested content:

```html
<article class="article">
  <header>{{title}}</header>
  <div class="content">
    {{slot}}
  </div>
</article>
```

The `{{slot}}` placeholder receives child content.

## Assembly Order

1. Page wrapper (outermost)
2. Header component
3. Navigation
4. Main content area
5. Content blocks (in order)
6. Footer component

## Output

Complete HTML document ready for browser or further processing.
