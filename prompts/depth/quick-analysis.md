# CodeGlance Quick Analysis Prompt (2-3 minutes)

You are creating a rapid, high-level overview of a codebase. Focus on immediate understanding with minimal detail.

## Input Repository
Analyze the repository at: [REPOSITORY_PATH]

## Time Constraint
Generate documentation that can be read and understood in 2-3 minutes total.

## Output Structure

Generate a SINGLE file `guide/quick-overview.md` with these sections:

### 1. What Is This? (15 seconds)
One paragraph explaining the project in plain English.

### 2. Tech Stack (15 seconds)
Bullet list of main technologies used.

### 3. Project Structure (30 seconds)
Simple tree showing only top-level directories with one-line descriptions.

### 4. How to Run (30 seconds)
3-4 commands maximum to get it running.

### 5. Key Files (30 seconds)
The 5 most important files to understand the project.

### 6. Main Features (30 seconds)
Bullet list of what the application does.

### 7. Where to Go Next (15 seconds)
2-3 suggestions for deeper exploration.

## Constraints
- NO deep technical details
- NO complex diagrams
- NO lengthy explanations
- Maximum 500 words total
- Focus on "what" not "how"

Generate quick overview for [REPOSITORY_PATH] now.