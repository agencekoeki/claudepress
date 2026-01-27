# Design System

## Overview

This document defines the design tokens and visual rules for the theme.

## Color Palette

### Primary Colors
```
--color-primary: #007bff
--color-primary-light: #4da3ff
--color-primary-dark: #0056b3
```

### Neutral Colors
```
--color-neutral-100: #f8f9fa
--color-neutral-200: #e9ecef
--color-neutral-300: #dee2e6
--color-neutral-400: #ced4da
--color-neutral-500: #adb5bd
--color-neutral-600: #6c757d
--color-neutral-700: #495057
--color-neutral-800: #343a40
--color-neutral-900: #212529
```

### Semantic Colors
```
--color-success: #28a745
--color-warning: #ffc107
--color-error: #dc3545
--color-info: #17a2b8
```

## Typography

### Font Families
```
--font-family-base: system-ui, -apple-system, sans-serif
--font-family-heading: var(--font-family-base)
--font-family-mono: 'SF Mono', 'Consolas', monospace
```

### Font Sizes
```
--font-size-xs: 0.75rem
--font-size-sm: 0.875rem
--font-size-base: 1rem
--font-size-lg: 1.125rem
--font-size-xl: 1.25rem
--font-size-2xl: 1.5rem
--font-size-3xl: 2rem
--font-size-4xl: 2.5rem
```

### Line Heights
```
--line-height-tight: 1.25
--line-height-base: 1.5
--line-height-relaxed: 1.75
```

## Spacing

```
--spacing-xs: 0.25rem
--spacing-sm: 0.5rem
--spacing-md: 1rem
--spacing-lg: 1.5rem
--spacing-xl: 2rem
--spacing-2xl: 3rem
--spacing-3xl: 4rem
```

## Borders

```
--border-radius-sm: 0.25rem
--border-radius-md: 0.5rem
--border-radius-lg: 1rem
--border-radius-full: 9999px

--border-width: 1px
--border-color: var(--color-neutral-300)
```

## Shadows

```
--shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.05)
--shadow-md: 0 4px 6px rgba(0, 0, 0, 0.1)
--shadow-lg: 0 10px 15px rgba(0, 0, 0, 0.1)
```

## Breakpoints

```
--breakpoint-sm: 640px
--breakpoint-md: 768px
--breakpoint-lg: 1024px
--breakpoint-xl: 1280px
```

## Usage Guidelines

1. Always use design tokens instead of hard-coded values
2. Maintain consistent spacing using the spacing scale
3. Use semantic color names for UI states
4. Follow the type scale for visual hierarchy
