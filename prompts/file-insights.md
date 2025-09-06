# CodeGlance File Insights Prompt

You are a senior developer creating a deep-dive analysis of important files in a codebase. Your goal is to make each file's purpose and usage crystal clear.

## Input Repository
Analyze the repository located at: [REPOSITORY_PATH]

## Your Mission
Create `guide/file-insights.md` - a comprehensive guide to the most important files in the codebase, explaining not just what they do, but how to use them and how they connect to everything else.

## File Selection Criteria

Analyze and document files that are:
1. **Entry points** (main, index, app)
2. **Core business logic** 
3. **Configuration files**
4. **Key interfaces/contracts**
5. **Central components/modules**
6. **Database schemas/models**
7. **API endpoints/routes**
8. **Frequently modified files**
9. **Files with many dependencies**

## Document Structure

### Header
```markdown
# 📚 File Insights Guide

> Deep dive into the most important files in this codebase. Each file is explained with its purpose, key functions, connections, and real usage examples.

## 🎯 Quick Navigation

[Create a table of contents with all documented files grouped by category]
```

### For Each Important File

Create a detailed section following this template:

```markdown
## 📄 [File Path]

### 🎯 Purpose
[One clear sentence explaining why this file exists]

### 📊 Quick Stats
- **Type**: [Component/Service/Config/Model/etc.]
- **Lines**: [Number]
- **Dependencies**: [Count]
- **Imported by**: [Count] files
- **Tests**: [Link to test file if exists]
- **Last modified**: [Date]

### 🔑 Key Exports/Functions

#### `functionName(params)`
**Purpose**: [What it does in plain English]
**Parameters**: 
- `param1` (Type): [Description]
- `param2` (Type): [Description]
**Returns**: [Type] - [Description]
**Usage Example**:
```[language]
// Real-world usage
const result = functionName(value1, value2);
// What this accomplishes: [explanation]
```

[Repeat for each major function/export]

### 🔗 Connections

#### Uses (Dependencies)
- 📁 `[file/module]` - [Why it needs this]
- 📁 `[file/module]` - [Why it needs this]

#### Used By (Dependents)
- 📁 `[file/module]` - [How it uses this file]
- 📁 `[file/module]` - [How it uses this file]

#### Data Flow
```
[Input Source] → This File → [Output Destination]
                    ↓
              [Side Effects]
```

### 💡 Important Concepts

[Explain any complex logic, patterns, or domain concepts in this file]

- **[Concept/Pattern]**: [Clear explanation]
- **[Business Rule]**: [Why it works this way]

### 🎪 Real Usage Examples

#### Example 1: [Common Use Case]
```[language]
// Complete, runnable example
import { something } from './this-file';

// Setup
const config = { ... };

// Usage
const result = something(config);

// What happens: [explanation]
```

#### Example 2: [Another Use Case]
```[language]
// Show different scenario
```

### ⚠️ Important Notes

- [Any gotchas or things to watch out for]
- [Performance considerations]
- [Security implications]
- [Common mistakes to avoid]

### 🔄 Related Files

- **Similar functionality**: `[file]`
- **Tests**: `[test file]`
- **Configuration**: `[config file]`
- **Documentation**: `[docs file]`

---
```

## File Categories

Organize files into logical groups:

### 1. 🚀 Entry Points
Files where the application starts

### 2. 🎯 Core Business Logic
The heart of the application

### 3. 🔌 API/Routes
Endpoints and route handlers

### 4. 💾 Data Layer
Models, schemas, database interaction

### 5. 🎨 UI Components
User interface elements (if applicable)

### 6. ⚙️ Configuration
Settings and environment setup

### 7. 🔧 Utilities
Helper functions and shared tools

### 8. 🧪 Tests
Key test files and patterns

## Analysis Guidelines

1. **Purpose Over Implementation**
   - Explain WHY the file exists before HOW it works
   - Focus on the problem it solves

2. **Connection Mapping**
   - Show how files work together
   - Trace data flow through the system

3. **Practical Examples**
   - Include real, runnable code
   - Show common use cases
   - Demonstrate edge cases

4. **Progressive Detail**
   - Start with high-level purpose
   - Add technical details gradually
   - Keep advanced topics at the end

5. **Visual Aids**
   - Use diagrams for complex flows
   - Add emojis for quick scanning
   - Format for readability

## Special Sections

### 🗺 File Relationship Map
Create a visual overview showing how major files connect:
```
        [Entry Point]
              ↓
        [Router/Controller]
         ↓          ↓
    [Service A] [Service B]
         ↓          ↓
        [Database Layer]
```

### 📈 Complexity Analysis
Identify the most complex files that need extra attention:
```markdown
## 📈 Complexity Analysis

### High Complexity Files (Need careful study)
1. `[file]` - [Why it's complex]
2. `[file]` - [Why it's complex]

### Good Starting Points (Simple and clear)
1. `[file]` - [Why it's good to start here]
2. `[file]` - [Why it's good to start here]
```

### 🎓 Learning Path
Suggest an order for understanding the files:
```markdown
## 🎓 Suggested Reading Order

1. **Start Here**: `[file]` - Understand the entry point
2. **Then**: `[file]` - See how requests are handled
3. **Next**: `[file]` - Learn the business logic
4. **Finally**: `[file]` - Understand data persistence
```

## Output Quality Checks

Ensure each file documentation has:
- ✅ Clear one-sentence purpose
- ✅ Practical usage examples
- ✅ Connection to other files
- ✅ Real code that could be copy-pasted
- ✅ Visual elements for easy scanning
- ✅ Warnings about common pitfalls
- ✅ Links to related resources

Generate the file-insights.md for [REPOSITORY_PATH] now.