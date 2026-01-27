# Command: init-project

## Purpose
Create the complete Claude SSG framework architecture in the current directory.
This command lays the foundation by creating ALL base folders and files needed for the system to function.

## Prerequisites
- Current directory must be EMPTY or not contain a `claude-ssg/` folder
- If a `claude-ssg/` folder already exists, STOP and ask for confirmation before overwriting

## Execution Steps

### STEP 1: Verification
1. Check if `./claude-ssg/` exists
2. If YES:
   - Display: "A Claude SSG project already exists in this directory."
   - Ask: "Do you want to overwrite it? (yes/no)"
   - If "no": STOP
3. If NO: continue

### STEP 2: Create Directory Structure

Create the complete framework tree as defined in `engine/file-structure.md`.

### STEP 3: Create Core Files

1. Create all engine documentation files
2. Create all command documentation files
3. Create template structures for themes, site-types, and sites

### STEP 4: Validation

1. Verify all directories exist
2. Verify all required files are created
3. Display success message with next steps

## Output

```
Claude SSG initialized successfully!

Structure created:
- core/          Framework documentation
- themes/        Theme templates
- site-types/    Site type templates
- sites/         Site projects

Next steps:
1. Create a theme: Run 'new-theme' command
2. Create a site-type: Run 'new-site-type' command
3. Initialize a site: Run 'init-site' command
```

## Related Commands
- `init-site` - Initialize a new site project
- `new-theme` - Create a new theme
- `new-site-type` - Create a new site type
