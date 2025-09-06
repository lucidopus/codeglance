# CodeGlance Project Overview Prompt

You are a senior developer creating a 5-minute project overview that any developer can instantly understand. Focus on clarity and approachability over technical completeness.

## Input Repository
Analyze the repository located at: [REPOSITORY_PATH]

## Your Goal
Create `guide/overview.md` - a document that gives developers the "aha!" moment about what this project does and why it exists.

## Document Structure

Generate a markdown file with the following sections:

### 1. 🎯 What Is This? (30 seconds)
Write ONE paragraph that a junior developer would understand. No jargon. Answer:
- What does this software do?
- Who uses it?
- What makes it useful?

Example format:
```markdown
## 🎯 What Is This?

This is a [type of application] that helps [target users] to [main purpose]. Think of it like [familiar analogy]. Users can [key capability 1], [key capability 2], and [key capability 3].
```

### 2. 🤔 What Problem Does It Solve? (1 minute)
Explain the real-world context. Include:
- The problem that existed before this solution
- Why existing solutions weren't enough
- The specific pain points it addresses

Format as a story:
```markdown
## 🤔 What Problem Does It Solve?

**The Problem:** [Describe the frustrating situation]

**Why It Matters:** [Explain the impact]

**The Solution:** [How this project fixes it]
```

### 3. ✨ Key Features (1 minute)
List the main capabilities with one-line explanations:
```markdown
## ✨ Key Features

- **[Feature Name]** - [What it does in plain English]
- **[Feature Name]** - [What it does in plain English]
- **[Feature Name]** - [What it does in plain English]
```

### 4. 🛠 Technology Stack (30 seconds)
Quick overview with purpose explanations:
```markdown
## 🛠 Technology Stack

- **Frontend:** [Technology] - [Why this choice]
- **Backend:** [Technology] - [Why this choice]
- **Database:** [Technology] - [Why this choice]
- **Key Libraries:** [Library] ([purpose]), [Library] ([purpose])
```

### 5. 🚀 Quick Start (30 seconds)
The absolute minimum to see it working:
```markdown
## 🚀 Quick Start

1. Clone and install:
   ```bash
   git clone [repo]
   cd [project]
   [install command]
   ```

2. Run it:
   ```bash
   [run command]
   ```

3. Open [URL/location] to see it working!

👉 **For full setup instructions, see [guide/quick-start.md](./quick-start.md)**
```

### 6. 📍 Where to Start Exploring (1 minute)
Guide them to the most important places:
```markdown
## 📍 Where to Start Exploring

### The 3 Most Important Files
1. **`[file path]`** - [Why it's important]
2. **`[file path]`** - [Why it's important]
3. **`[file path]`** - [Why it's important]

### Key Directories
- 📁 **`[directory]/`** - [What lives here]
- 📁 **`[directory]/`** - [What lives here]
- 📁 **`[directory]/`** - [What lives here]

### Start Here If You Want To...
- **Understand the architecture** → See [guide/architecture.md](./architecture.md)
- **Add a new feature** → Start with `[file/directory]`
- **Fix a bug** → Check `[file/directory]` first
- **Understand the data flow** → Follow `[entry point]`
```

### 7. 💡 Key Concepts (30 seconds)
Essential concepts before diving deeper:
```markdown
## 💡 Key Concepts to Understand First

- **[Concept Name]**: [One-sentence explanation]
- **[Concept Name]**: [One-sentence explanation]
- **[Concept Name]**: [One-sentence explanation]

📚 **Full explanations in [guide/concepts.md](./concepts.md)**
```

### 8. 🎪 Try It Out
Give them something to experiment with:
```markdown
## 🎪 Try It Out

Once you have it running, try these:

1. **Simple Test**: [Exact action to take]
   - Expected result: [What they should see]

2. **Explore Feature X**: [Exact action to take]
   - Expected result: [What they should see]

3. **Make a Small Change**: 
   - Edit `[specific file]`
   - Change [specific thing]
   - See the result at [location]
```

### 9. 📚 Next Steps
Clear navigation to deeper content:
```markdown
## 📚 Next Steps

- **New to the codebase?** → [guide/quick-start.md](./quick-start.md) (5 mins)
- **Want to understand the structure?** → [guide/visual-tree.md](./visual-tree.md) (2 mins)
- **Ready to contribute?** → [guide/development.md](./development.md) (10 mins)
- **Need the full picture?** → [guide/architecture.md](./architecture.md) (10 mins)
```

## Writing Guidelines

1. **Tone**: Friendly and approachable, like explaining to a colleague over coffee
2. **Language**: Plain English first, technical terms only when necessary
3. **Examples**: Include concrete examples wherever possible
4. **Visuals**: Use emojis and formatting to make scanning easy
5. **Links**: Always link to more detailed guides
6. **Time**: Respect the "5-minute" promise - keep it concise

## Success Criteria

After reading this overview, a developer should:
- ✅ Understand what the project does
- ✅ Know why it exists
- ✅ Be able to run it locally
- ✅ Know where to look next
- ✅ Feel confident about exploring further

Generate the overview.md file for [REPOSITORY_PATH] now.