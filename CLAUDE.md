# CLAUDE.md - AI Assistant Guide for claudepress

This document provides guidance for AI assistants working on the claudepress repository.

## Project Overview

**claudepress** is a project in its initial setup phase. The repository has been initialized but does not yet contain application code, build configuration, or development tooling.

### Current State

- **Status**: Fresh repository - awaiting initial project setup
- **Content**: Placeholder readme.md only
- **Dependencies**: None configured
- **Build System**: Not yet established

## Repository Structure

```
claudepress/
├── CLAUDE.md          # This file - AI assistant guidance
├── readme.md          # Project readme (placeholder)
└── .git/              # Git repository configuration
```

As the project develops, this section should be updated to reflect the actual codebase structure.

## Development Guidelines

### Git Workflow

1. **Branch Naming**: Feature branches should follow the pattern `claude/<feature-name>-<session-id>`
2. **Commits**: Write clear, descriptive commit messages that explain the "why" behind changes
3. **Main Branch**: Protected - all changes should go through feature branches
4. **Push Commands**: Always use `git push -u origin <branch-name>`

### Code Conventions

_To be established once the tech stack is chosen. Update this section with:_

- Language-specific style guides
- Linting and formatting rules
- Naming conventions
- File organization patterns

### Testing Requirements

_To be established. Update this section with:_

- Test framework and runner
- Coverage requirements
- Test file naming and location conventions
- Instructions for running tests

### Build & Development

_To be established. Update this section with:_

- Development environment setup
- Build commands
- Local development server instructions
- Environment variables and configuration

## For AI Assistants

### Before Making Changes

1. **Read First**: Always read files before modifying them
2. **Understand Context**: Explore related code to understand existing patterns
3. **Check Dependencies**: Verify any new dependencies are necessary and appropriate
4. **Maintain Consistency**: Follow existing code patterns and conventions

### When Writing Code

1. **Keep It Simple**: Avoid over-engineering; only add what's needed for the current task
2. **Security**: Never introduce vulnerabilities (injection, XSS, etc.)
3. **No Guessing**: Don't make assumptions about file contents or API behavior
4. **Document Changes**: Update relevant documentation when making significant changes

### When Committing

1. Use descriptive commit messages that explain the purpose of changes
2. Stage specific files rather than using `git add -A` or `git add .`
3. Never commit sensitive files (.env, credentials, etc.)
4. Include the Claude session link at the end of commit messages

### File Operations

- Prefer editing existing files over creating new ones
- Don't create documentation files unless explicitly requested
- Use appropriate tools for file operations (Read, Edit, Write) instead of shell commands

## Project-Specific Notes

_Add project-specific guidance here as the codebase develops:_

- Key architectural decisions and their rationale
- Important modules and their responsibilities
- Common pitfalls or gotchas
- Integration points and external dependencies
- Performance considerations

## Quick Reference

### Common Commands

```bash
# To be populated when build system is configured
# Example commands:
# npm install        - Install dependencies
# npm run dev        - Start development server
# npm test           - Run tests
# npm run build      - Production build
```

### Important Files

| File | Purpose |
|------|---------|
| `CLAUDE.md` | AI assistant guidance (this file) |
| `readme.md` | Project documentation |
| _More to be added_ | _As project develops_ |

### Key Contacts / Resources

_To be added:_
- Project documentation links
- API documentation
- Design system / UI guidelines
- Deployment documentation

---

**Last Updated**: 2026-01-27
**Repository**: claudepress
**Status**: Initial Setup Phase
