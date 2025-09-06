# CodeGlance Structured Markdown Output Prompt

You are generating well-structured, scannable markdown documentation optimized for readability and navigation.

## Input Repository
Analyze the repository at: [REPOSITORY_PATH]

## Markdown Formatting Guidelines

### Structure Rules
- Use clear heading hierarchy (# ## ### ####)
- Include table of contents for long documents
- Use emoji markers for visual scanning
- Create collapsible sections for details
- Add navigation links between related docs

### Visual Elements
```markdown
## 📚 Section with Emoji Marker

### ✅ Success Indicators
- Clear checkmarks for positive items
- ❌ Clear X for negative items
- ⚠️ Warnings that stand out
- 💡 Tips and insights

### 📊 Data Tables
| Column | Description | Example |
|--------|-------------|---------|
| Clean | Aligned | Data |

### 📝 Code Blocks
\```language
// Syntax highlighted code
const example = "with proper language tags";
\```

### 🔗 Cross-References
See [Related Section](#related-section) for more details.
```

## Output Requirements

### 1. Consistent Formatting
- Same heading styles throughout
- Consistent emoji usage
- Uniform code block styling
- Standard link formats

### 2. Navigation Aids
```markdown
<!-- At top of each file -->
[← Back to Overview](./overview.md) | [Next: Architecture →](./architecture.md)

## 📑 Table of Contents
- [Section 1](#section-1)
- [Section 2](#section-2)
```

### 3. Collapsible Details
```markdown
<details>
<summary>Click to expand detailed explanation</summary>

Detailed content here that doesn't clutter
the main document flow.

</details>
```

### 4. Visual Separators
```markdown
---

## New Major Section

***

### Subsection Separator
```

### 5. Highlighted Information
```markdown
> **Note:** Important information in blockquotes

> ⚠️ **Warning:** Critical warnings stand out

> 💡 **Tip:** Helpful suggestions

> ✅ **Success:** Confirmation messages
```

## File Structure Template
```markdown
# 📘 Document Title

> Brief description of what this document covers

## 📑 Table of Contents
[Generated TOC]

---

## 🎯 Overview
[Content]

## 📋 Main Content
[Structured sections]

## 📚 Related Documents
- [Link 1](./doc1.md) - Description
- [Link 2](./doc2.md) - Description

---

[← Previous](./prev.md) | [Home](./README.md) | [Next →](./next.md)
```

Generate structured markdown documentation for [REPOSITORY_PATH] now.