# Content Templates

## Overview

Content templates provide scaffolding for new content files. Use them with the `new-page` command.

## Usage

```
new-page <site-name> <page-path> --template=<template-name>
```

## Available Templates

_No content templates defined yet._

### Example Template Entry

To create a template, add a `.md` file to this directory:

**blog-post.md:**
```markdown
---
title: Post Title
date: {{date}}
author:
tags: []
excerpt:
template: post
---

# {{title}}

Introduction paragraph...

## Section 1

Content...

## Conclusion

Closing thoughts...
```

## Template Variables

Templates can use these variables:
- `{{date}}` - Current date
- `{{title}}` - Title from command or placeholder
- `{{slug}}` - URL slug
- `{{author}}` - Default author from site.json

## Creating New Templates

1. Create a `.md` file in this directory
2. Add frontmatter with required fields
3. Include placeholder content
4. Document the template in this file
