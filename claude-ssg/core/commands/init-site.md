# Command: init-site

## Purpose
Initialize a new site project within the Claude SSG framework.

## Syntax
```
init-site <site-name> --theme=<theme> --type=<site-type>
```

## Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| site-name | Yes | Unique site identifier (kebab-case) |
| --theme | Yes | Theme to use |
| --type | Yes | Site type preset to use |

## Prerequisites
- Claude SSG framework must be initialized
- Specified theme must exist in `themes/`
- Specified site-type must exist in `site-types/`
- Site name must not already exist in `sites/`

## Execution Steps

### STEP 1: Validation
1. Verify framework exists
2. Verify theme exists
3. Verify site-type exists
4. Verify site name is available

### STEP 2: Create Site Structure
Copy from `sites/_template/` to `sites/<site-name>/`:
```
sites/<site-name>/
├── site.json
├── content/
│   └── index.md
├── overrides/
│   ├── components/
│   └── ux-tweaks.md
├── public/
└── _state/
    └── manifest.json
```

### STEP 3: Configure Site
Update `site.json` with:
```json
{
  "name": "<site-name>",
  "theme": "<theme>",
  "siteType": "<site-type>",
  "url": "",
  "language": "en",
  "created": "<timestamp>"
}
```

### STEP 4: Initialize Content
Create default index.md with frontmatter from site-type template.

## Output
```
Site '<site-name>' created successfully!

Configuration:
- Theme: <theme>
- Type: <site-type>
- Location: sites/<site-name>/

Next steps:
1. Edit site.json to configure your site
2. Add content in content/
3. Run 'build <site-name>' to generate output
```

## Related Commands
- `build` - Build the site
- `new-page` - Add a new page
- `validate` - Validate site configuration
