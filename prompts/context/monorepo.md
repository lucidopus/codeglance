# CodeGlance Monorepo Analysis Prompt

You are analyzing a monorepo containing multiple packages/projects. Focus on package relationships and shared infrastructure.

## Input Repository
Analyze the monorepo at: [REPOSITORY_PATH]

## Monorepo-Specific Analysis

### Key Areas
- Package organization strategy
- Dependency management
- Shared code and utilities
- Build orchestration
- Cross-package testing

## Output Structure

Generate the following in `guide/monorepo/`:

### 1. guide/monorepo/overview.md
```markdown
# 📦 Monorepo Structure

## Packages Overview
| Package | Type | Purpose | Dependencies |
|---------|------|---------|--------------|
| [name] | [app/lib] | [purpose] | [deps] |

## Workspace Configuration
- Tool: [Lerna/Yarn/PNPM/Nx/Rush]
- Package manager: [npm/yarn/pnpm]
- Shared dependencies location
```

### 2. guide/monorepo/packages.md
For each package:
- Package purpose and responsibility
- Public API/exports
- Internal dependencies
- External dependencies
- Build configuration

### 3. guide/monorepo/shared-code.md
- Common utilities location
- Shared components/modules
- Shared configurations
- Shared types/interfaces
- Cross-package contracts

### 4. guide/monorepo/dependency-graph.md
Visual and textual dependency map:
```
app-frontend → lib-ui → lib-core
     ↓           ↓         ↓
app-backend → lib-api → lib-database
```

### 5. guide/monorepo/development.md
- How to work across packages
- Running specific packages
- Cross-package testing
- Building and publishing
- Version management

### 6. guide/monorepo/ci-cd.md
- Build optimization strategies
- Affected package detection
- Parallel build configuration
- Deploy coordination
- Release strategies

## Special Considerations
- Identify circular dependencies
- Document package boundaries
- Explain code sharing strategy
- Note performance implications
- Migration paths for new packages

Generate monorepo analysis for [REPOSITORY_PATH] now.