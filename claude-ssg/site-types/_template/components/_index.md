# Site Type Components

## Overview

This directory contains components specific to this site type. These components extend or override theme components.

## Component Hierarchy

Components are resolved in this order:
1. Site overrides (`sites/{site}/overrides/components/`)
2. **Site type components** (`site-types/{type}/components/`) ← This directory
3. Theme components (`themes/{theme}/components/`)

## Adding Components

To add a site-type specific component:

1. Create `{component-name}.html` in this directory
2. Document it below
3. Components here will be used instead of theme components with the same name

## Available Components

_No site-type specific components defined yet._

### Example Component Entry

```markdown
### component-name

**Purpose:** What this component does

**Props:**
- prop1: Description
- prop2: Description

**Slots:**
- slot: Main content area

**Usage:**
::component-name
  prop1: value
::
```
