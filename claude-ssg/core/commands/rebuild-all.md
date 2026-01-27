# Command: rebuild-all

## Purpose
Force a complete rebuild of a site, ignoring cache and state.

## Syntax
```
rebuild-all <site-name> [--clean]
```

## Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| site-name | Yes | Site to rebuild |
| --clean | No | Delete output directory first |

## Prerequisites
- Site must exist
- Site must be valid (or use --force to skip validation)

## Execution Steps

### STEP 1: Clean State
1. Clear `_state/manifest.json`
2. If --clean: delete `public/` contents

### STEP 2: Full Build
1. Process ALL content files (ignore cache)
2. Regenerate ALL output files
3. Re-copy ALL assets

### STEP 3: Update State
Create fresh `manifest.json` with all files.

## When to Use

- After theme changes that affect all pages
- After component modifications
- When build state is corrupted
- After upgrading framework

## Output
```
Rebuilding site '<site-name>' from scratch...

Clearing state...
Processing all content files...
  content/index.md → index.html
  content/about.md → about/index.html
  content/blog/post-1.md → blog/post-1/index.html

Copying all assets...

Rebuild complete!
- Pages: 3
- Assets: 12
- Duration: 1.2s
```

## Comparison with `build`

| Aspect | build | rebuild-all |
|--------|-------|-------------|
| Uses cache | Yes | No |
| Incremental | Yes | No |
| Speed | Fast | Slower |
| Use when | Regular builds | Major changes |

## Related Commands
- `build` - Incremental build
- `validate` - Validate before rebuild
