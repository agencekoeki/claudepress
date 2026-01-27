# Command: diff

## Purpose
Compare files between theme, site-type, and site overrides.

## Syntax
```
diff <site-name> <component-name>
diff <site-name> --all
```

## Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| site-name | Yes | Site context |
| component-name | Yes* | Component to compare |
| --all | No | Show all overrides |

## Use Cases

1. See what you've changed from the original theme
2. Review all customizations in a site
3. Decide whether to update or remove overrides

## Execution Steps

### STEP 1: Locate Files
Find component in:
1. `sites/{site}/overrides/components/` (override)
2. `site-types/{type}/components/` (type layer)
3. `themes/{theme}/components/` (theme layer)

### STEP 2: Compare
Generate diff between override and original

### STEP 3: Display

## Output

### Single Component
```
Diff: header.html
=================

Original: themes/minimal/components/header.html
Override: sites/my-site/overrides/components/header.html

--- original
+++ override
@@ -1,5 +1,7 @@
 <header class="header">
-  <nav class="header__nav">
+  <div class="header__logo">
+    <img src="{{site.logo}}" alt="{{site.name}}">
+  </div>
+  <nav class="header__nav header__nav--right">
     {{slot}}
   </nav>
 </header>
```

### All Overrides (--all)
```
Site Overrides: my-site
=======================

Components:
  header.html    +12 -3 lines
  footer.html    +5 -2 lines

UX Tweaks:
  ux-tweaks.md   Custom navigation behavior

Total: 2 component overrides, 1 UX override
```

## Related Commands
- `override-component` - Create override
- `override-ux` - Create UX override
