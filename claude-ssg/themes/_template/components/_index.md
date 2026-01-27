# Theme Components

## Overview

This document lists all components available in this theme.

## Layout Components

### page-wrapper
The outermost container for all pages.

**Props:**
- `slot`: Page content

### header
Site header with navigation.

**Props:**
- `slot`: Navigation items

### footer
Site footer.

**Props:**
- `slot`: Footer content

### nav
Navigation container.

**Props:**
- `slot`: Navigation items

### nav-item
Individual navigation link.

**Props:**
- `href`: Link URL
- `text`: Link text
- `active`: Boolean for current page

## Content Components

### article
Article/post container.

**Props:**
- `title`: Article title
- `slot`: Article content

### article-card
Card preview of an article.

**Props:**
- `title`: Article title
- `excerpt`: Short description
- `href`: Link to full article
- `date`: Publication date

### heading
Section headings (h1-h6).

**Props:**
- `level`: Heading level (1-6)
- `text`: Heading text

### paragraph
Text paragraphs.

**Props:**
- `text`: Paragraph content

### link
Inline links.

**Props:**
- `href`: Link URL
- `text`: Link text

### button
Clickable buttons.

**Props:**
- `text`: Button text
- `href`: Optional link
- `variant`: primary, secondary, outline

### image
Images with optional caption.

**Props:**
- `src`: Image source
- `alt`: Alt text
- `caption`: Optional caption

### list
Ordered or unordered lists.

**Props:**
- `ordered`: Boolean
- `items`: Array of items

### list-item
Individual list item.

**Props:**
- `text`: Item content

### blockquote
Quoted text.

**Props:**
- `text`: Quote content
- `cite`: Optional citation

### code-block
Multi-line code.

**Props:**
- `code`: Code content
- `language`: Programming language

### code-inline
Inline code.

**Props:**
- `code`: Code content

### divider
Horizontal rule/separator.

No props.
