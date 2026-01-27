# Command: build

## Purpose
Generate static HTML output for a site.

## Syntax
```
build <site-name> [--output=<path>] [--clean]
```

## Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| site-name | Yes | Site to build |
| --output | No | Output directory (default: sites/{site}/public/) |
| --clean | No | Clean output directory before build |

## Prerequisites
- Site must exist and be valid
- Theme must exist
- Site-type must exist

## Execution Steps

### STEP 1: Validation
1. Run `validate <site-name>`
2. If errors: STOP and display errors
3. If warnings: display and continue

### STEP 2: Load Configuration
1. Load `site.json`
2. Load theme `design-system.md`
3. Load site-type `ux-system.md`

### STEP 3: Process Content
For each `.md` file in `content/`:
1. Parse with parser engine
2. Resolve variables
3. Apply components via assembler
4. Generate HTML output

### STEP 4: Copy Assets
1. Copy theme assets to output
2. Copy site public/ assets
3. Process CSS variables if needed

### STEP 5: Update State
Update `_state/manifest.json`:
```json
{
  "lastBuild": "<timestamp>",
  "files": [
    {"source": "content/index.md", "output": "index.html", "hash": "..."}
  ],
  "status": "success"
}
```

## Output
```
Building site '<site-name>'...

Processing:
  content/index.md → index.html
  content/about.md → about/index.html

Copying assets...

Build complete!
- Pages: 2
- Assets: 5
- Output: sites/<site-name>/public/
```

## Related Commands
- `validate` - Validate before building
- `rebuild-all` - Force rebuild all files
- `preview` - Preview built site
