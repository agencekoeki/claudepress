# Command: preview

## Purpose
Preview a built site locally before deployment.

## Syntax
```
preview <site-name> [--port=<port>]
```

## Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| site-name | Yes | Site to preview |
| --port | No | Port number (default: 8080) |

## Prerequisites
- Site must exist
- Site must be built

## Execution Steps

### STEP 1: Validation
1. Verify site exists
2. Verify `public/` directory has content
3. If not built: suggest running `build` first

### STEP 2: Start Server
Start local HTTP server serving `sites/{site}/public/`

### STEP 3: Display Information

## Output
```
Starting preview server...

Site:    my-site
URL:     http://localhost:8080
Root:    sites/my-site/public/

Press Ctrl+C to stop.

---
Serving files...
GET /index.html 200
GET /css/style.css 200
GET /about/index.html 200
```

## Preview Features

- Live directory listing
- Proper MIME types
- Clean URLs (/about/ → /about/index.html)
- 404 page handling

## Notes

This is a development preview only:
- Not for production use
- No HTTPS
- No caching headers
- Single connection

For production, export and deploy to a proper hosting service.

## Related Commands
- `build` - Build before preview
- `export` - Export for deployment
