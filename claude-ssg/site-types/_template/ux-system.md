# UX System

## Overview

This document defines the user experience patterns and behaviors for this site type.

## Navigation Patterns

### Primary Navigation
- Position: Top header
- Behavior: Static
- Mobile: Hamburger menu

### Secondary Navigation
- Position: Footer
- Content: Utility links

## Page Layouts

### Default Layout
```
+------------------+
|     Header       |
+------------------+
|                  |
|   Main Content   |
|                  |
+------------------+
|     Footer       |
+------------------+
```

## Interactions

### Links
- Underline on hover
- Focus visible outline

### Buttons
- Hover state: darken
- Active state: pressed effect
- Focus: visible outline

### Forms
- Labels above inputs
- Inline validation
- Clear error messages

## Animations

### Page Transitions
- None by default

### Component Animations
- Subtle fade for modals
- Smooth scroll for anchors

## Accessibility Requirements

### Keyboard Navigation
- All interactive elements focusable
- Logical tab order
- Skip links for main content

### Screen Readers
- Semantic HTML structure
- ARIA labels where needed
- Live regions for dynamic content

### Visual
- Minimum contrast ratio: 4.5:1
- Focus indicators visible
- No motion for reduced-motion preference

## Responsive Behavior

### Breakpoints
- Mobile: < 640px
- Tablet: 640px - 1024px
- Desktop: > 1024px

### Mobile Considerations
- Touch-friendly targets (44x44px min)
- No hover-dependent functionality
- Simplified navigation
