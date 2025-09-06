# Codeglance Command

Execute a comprehensive code analysis workflow on a GitHub repository. This command clones a repository and runs a complete analysis using the available prompts.

## Usage

```
/codeglance <github_url>
```

**Example:**
```
/codeglance https://github.com/username/repository-name
```

## Workflow Overview

This command orchestrates the following sequential workflow:

1. **Repository Cloning** - Clone the GitHub repository to `repos/` directory
2. **Sequential Prompt Execution** - Run analysis prompts in optimal order
3. **Comprehensive Analysis** - Generate complete documentation and insights

## Execution Steps

### 1. Repository Setup
- Create `repos/` directory if it doesn't exist
- Clone the provided GitHub repository
- Navigate to the cloned repository directory
- Verify repository structure and identify project type

### 2. Sequential Prompt Execution

Execute the following prompts in optimal order for best understanding:

#### 01-project-overview: Foundation Understanding
Execute `/project-overview` to generate:
- High-level project understanding and purpose
- Technology stack identification
- Key features and functionality overview
- Problem context and solution approach

**Output:** `guide/overview.md`

#### 02-visual-tree: Structure Mapping  
Execute `/visual-tree` to create:
- Complete directory tree visualization with icons
- File organization insights and patterns
- Important file identification and purpose
- Structure recommendations and navigation

**Output:** `guide/tree.md`

#### 03-file-insights: Deep File Analysis
Execute `/file-insights` to provide:
- Critical file analysis with usage examples
- Key functions and their purposes
- File connections and dependencies
- Code patterns and best practices

**Output:** `guide/file-insights.md`

#### 04-architecture: System Design
Execute `/architecture` to create:
- System architecture documentation with diagrams
- Component relationships and data flow
- Design patterns and architectural decisions
- API design and database schema

**Output:** `guide/architecture.md`

#### 05-quick-start: Developer Onboarding
Execute `/quick-start` to generate:
- Step-by-step setup instructions
- Prerequisites and environment configuration
- Common commands and troubleshooting
- First changes and verification steps

**Output:** `guide/quick-start.md`

#### 06-master-analysis: Comprehensive Synthesis
Execute `/master-analysis` to create:
- Complete documentation suite generation
- Cross-referencing between all guides
- Executive summary and key insights
- Navigation and learning paths

**Output:** Multiple interconnected guide files

## Implementation Instructions

When executing this command:

### Repository Cloning Process
1. Validate the GitHub URL format
2. Extract repository name from URL
3. Create `repos/` directory: `mkdir -p repos`
4. Clone repository: `git clone <github_url> repos/<repo_name>`
5. Navigate to repository: `cd repos/<repo_name>`
6. Verify successful clone and repository health

### Sequential Execution
1. Execute prompts in the numbered order (01 → 02 → 03 → 04 → 05 → 06)
2. Wait for each prompt to complete before proceeding to next
3. Capture and preserve outputs from each step with timestamps
4. Handle any errors gracefully and report status
5. Maintain execution log showing progress through all 6 steps

### Error Handling
- If cloning fails, provide clear error message and troubleshooting steps
- If any prompt fails, continue with remaining prompts but note the failure
- Provide summary of successful and failed operations
- Suggest manual execution steps for failed prompts

### Output Organization
- Create a `codeglance-results/` directory in the repository
- Save each prompt's output with timestamp
- Generate a master index of all analysis results
- Provide quick navigation links between analyses

## Pre-execution Checks

Before starting the workflow:
1. Verify GitHub URL is valid and accessible
2. Check if repository already exists in `repos/` directory
3. Ensure sufficient disk space for cloning
4. Verify git is installed and configured

## Post-execution Summary

After completion, provide:
- Summary of all executed steps
- Links to generated documentation
- Key insights and findings
- Recommended next steps
- Quick access commands for reviewing results

## Command Options

**Basic Usage:**
```
/codeglance https://github.com/user/repo
```

**With specific branch:**
```
/codeglance https://github.com/user/repo -b branch-name
```

## Expected Outputs

This workflow will generate documentation in sequential order:
1. `guide/overview.md` - Project foundation and purpose (01-project-overview)
2. `guide/tree.md` - Visual directory structure (02-visual-tree)
3. `guide/file-insights.md` - Critical file deep-dive (03-file-insights)
4. `guide/architecture.md` - System design and patterns (04-architecture)
5. `guide/quick-start.md` - Developer onboarding guide (05-quick-start)
6. Complete guide suite with cross-references (06-master-analysis)

## Integration Notes

- All prompts are designed to work together cohesively
- Each step builds upon previous analysis results
- Final master analysis synthesizes all findings
- Generated documentation follows consistent formatting
- Cross-references between documents are maintained

## Success Criteria

A successful codeglance execution should:
- Clone repository without errors
- Execute all 6 prompts successfully
- Generate complete documentation suite
- Provide actionable insights and recommendations
- Create navigable documentation structure