# Command: new-site-type

## Purpose
Create a new site type preset.

## Syntax
```
new-site-type <type-name> [--from=<base-type>]
```

## Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| type-name | Yes | Site type identifier (kebab-case) |
| --from | No | Base type to copy from |

## Prerequisites
- Type name must not already exist
- Base type must exist if specified

## Execution Steps

### STEP 1: Validation
1. Verify type name is valid (kebab-case)
2. Verify type doesn't exist
3. Verify base type if specified

### STEP 2: Create Structure
Copy from `site-types/_template/` to `site-types/<type-name>/`:

```
site-types/<type-name>/
├── preset.json
├── ux-system.md
├── structure.md
├── components/
│   └── _index.md
└── content-templates/
    └── _index.md
```

### STEP 3: Configure Type
Update `preset.json`:
```json
{
  "name": "<type-name>",
  "description": "",
  "requiredComponents": [],
  "defaultPages": ["index"],
  "created": "<timestamp>"
}
```

### STEP 4: Initialize Documentation
- Create `ux-system.md` with UX patterns
- Create `structure.md` with page structure rules

## Output
```
Site type '<type-name>' created successfully!

Location: site-types/<type-name>/

Next steps:
1. Edit preset.json with configuration
2. Define UX patterns in ux-system.md
3. Define page structure in structure.md
4. Add content templates in content-templates/
```

## Related Commands
- `list-site-types` - List available types
- `init-site` - Create site using type
