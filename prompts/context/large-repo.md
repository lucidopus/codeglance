# CodeGlance Large Repository Analysis Prompt (500+ files)

You are analyzing a large codebase. Focus on high-level organization and navigation rather than file-by-file details.

## Input Repository
Analyze the large repository at: [REPOSITORY_PATH]

## Strategy for Large Codebases

### Sampling Approach
- Analyze representative files from each module
- Focus on entry points and interfaces
- Identify patterns rather than documenting every file
- Create navigation aids for exploration

## Output Structure

Generate the following in `guide/`:

### 1. guide/navigation.md
```markdown
# 🗺️ Repository Navigation Guide

## Quick Jump Points
- Main entry: [file]
- Configuration: [directory]
- Business logic: [directory]
- Tests: [directory]
- Documentation: [directory]

## Module Map
[High-level module organization with purpose of each]

## Finding Things
- Features are in: [pattern]
- Tests follow: [pattern]
- Config files: [pattern]
```

### 2. guide/module-overview.md
Document major modules/packages:
- Module purpose and boundaries
- Key interfaces/contracts
- Dependencies between modules
- Module owners/teams (if evident)

### 3. guide/code-patterns.md
Identify recurring patterns:
- Naming conventions
- File organization patterns
- Common abstractions
- Architectural patterns

### 4. guide/hotspots.md
Identify important areas:
- Most modified files (high churn)
- Central integration points
- Complex areas needing attention
- Performance-critical paths

### 5. guide/search-guide.md
Help developers find things:
- "Looking for X? Check Y"
- Common search patterns
- Grep/find commands for common tasks
- IDE navigation tips

## Analysis Optimizations
- Use file patterns to understand structure
- Sample similar files rather than reading all
- Focus on public interfaces
- Create indices for navigation
- Identify code generation patterns

Generate large repository analysis for [REPOSITORY_PATH] now.