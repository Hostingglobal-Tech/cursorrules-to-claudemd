# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

```bash
# Install dependencies
pnpm install

# Build the project
pnpm build

# Run in development mode
pnpm dev

# Run tests
pnpm test

# Run specific test file
pnpm test src/__tests__/application/services/FileExplorerService.test.ts

# Run tests in watch mode
pnpm test:watch

# Run tests with coverage
pnpm test:coverage

# Publish to npm
pnpm publish:npm
```

## Architecture Overview

This project converts Cursor IDE rule files (`.mdc`) to Claude AI-compatible markdown using a **Layered Architecture**:

1. **Presentation Layer** (`src/presentation/`): CLI interface using Commander.js
2. **Application Layer** (`src/application/services/`): Core business logic
   - `FileExplorerService`: Recursively finds `.cursor` directories and `.mdc` files
   - `MetadataParserService`: Extracts YAML frontmatter from `.mdc` files
   - `FileConverterService`: Converts files and strips metadata, manages output directories
   - `AdvancedRootFileGeneratorService`: Generates categorized `_root.md` index
   - `ClaudeMdService`: Updates or creates CLAUDE.md files with `

<c2c-rules>
- @c2c-rules/_root.md
</c2c-rules>