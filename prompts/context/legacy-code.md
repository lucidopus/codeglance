# CodeGlance Legacy Code Analysis Prompt

You are analyzing a legacy codebase. Focus on understanding existing patterns, identifying technical debt, and providing modernization paths.

## Input Repository
Analyze the legacy codebase at: [REPOSITORY_PATH]

## Legacy Code Considerations

### Analysis Focus
- Identify outdated patterns
- Find security vulnerabilities
- Locate performance issues
- Document undocumented behavior
- Suggest incremental improvements

## Output Structure

Generate the following in `guide/legacy/`:

### 1. guide/legacy/overview.md
```markdown
# ⚠️ Legacy System Overview

## System Age & History
- Original creation date
- Major technology versions
- Last significant update
- Current maintenance status

## Technology Stack Assessment
| Technology | Version | Status | Risk Level |
|------------|---------|--------|------------|
| [tech] | [version] | [EOL/Supported] | [High/Med/Low] |

## Critical Issues
1. [Security vulnerability]
2. [Performance bottleneck]
3. [Maintenance blocker]
```

### 2. guide/legacy/understand-first.md
Document complex/undocumented areas:
- Business logic explanation
- Workarounds and hacks (with context)
- Hidden dependencies
- Assumed knowledge
- Magic numbers/strings explained

### 3. guide/legacy/technical-debt.md
Catalog technical debt:
- Code smells and anti-patterns
- Duplicated code locations
- Dead code identification
- Inconsistent patterns
- Missing tests

### 4. guide/legacy/modernization-plan.md
Incremental improvement strategy:
```markdown
## Phase 1: Stabilize (Low Risk)
- Add missing tests
- Document critical paths
- Fix security issues

## Phase 2: Refactor (Medium Risk)
- Extract reusable modules
- Update dependencies safely
- Standardize patterns

## Phase 3: Modernize (Higher Risk)
- Migrate to modern framework
- Rewrite critical components
- Update infrastructure
```

### 5. guide/legacy/danger-zones.md
Areas requiring special care:
- Fragile code sections
- Complex interdependencies
- Performance-critical paths
- Data migration risks
- Integration points

### 6. guide/legacy/working-with.md
Practical guidance:
- Safe change patterns
- Testing strategies
- Debugging approaches
- Common issues and fixes
- Who to ask (if evident from commits)

## Special Considerations
- Preserve working behavior documentation
- Identify regression risks
- Note missing source control history
- Document tribal knowledge
- Provide gradual migration paths

Generate legacy code analysis for [REPOSITORY_PATH] now.