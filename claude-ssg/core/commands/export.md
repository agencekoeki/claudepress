# Command: export

## Purpose
Export a built site for deployment or archiving.

## Syntax
```
export <site-name> [--format=<format>] [--output=<path>]
```

## Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| site-name | Yes | Site to export |
| --format | No | zip, tar, folder (default: zip) |
| --output | No | Output path (default: ./{site}.{ext}) |

## Prerequisites
- Site must exist
- Site must be built (run `build` first)

## Execution Steps

### STEP 1: Validation
1. Verify site exists
2. Verify site has been built
3. Verify output path is writable

### STEP 2: Gather Files
Collect from `sites/{site}/public/`:
- All HTML files
- All CSS/JS assets
- All images and media
- Any other static files

### STEP 3: Package
Based on format:
- **zip**: Create compressed archive
- **tar**: Create tarball (.tar.gz)
- **folder**: Copy to destination folder

### STEP 4: Generate Manifest
Include `_export-manifest.json`:
```json
{
  "site": "my-site",
  "exported": "<timestamp>",
  "files": 42,
  "size": "2.4 MB",
  "buildHash": "abc123"
}
```

## Output
```
Exporting site 'my-site'...

Format: zip
Files:  42
Size:   2.4 MB

Export complete!
Output: ./my-site.zip

Ready for deployment.
```

## Deployment Notes

The exported package contains:
- Static HTML (ready for any web server)
- All assets (CSS, JS, images)
- No server-side dependencies

Compatible with:
- Netlify, Vercel, GitHub Pages
- Any static file hosting
- Traditional web servers

## Related Commands
- `build` - Build before export
- `preview` - Preview before export
