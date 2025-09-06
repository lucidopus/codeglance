# CodeGlance

From Code to Clarity: Understand any GitHub repository in minutes.

CodeGlance is a tool that transforms GitHub repositories into intuitive, visual interfaces to help developers quickly understand unfamiliar codebases. Users paste a GitHub repository URL and get a user-friendly exploration interface.

## The Idea Behind CodeGlance

The core idea is to significantly reduce the time and effort developers spend trying to understand a new codebase. Instead of manually cloning repositories and piecing together the architecture, CodeGlance provides a high-level, interactive, and AI-powered overview. It's designed to feel like having an experienced team member guiding you through the code.

## Key Features

### Quick Wins (Low Effort)

These are features that can be implemented quickly to provide immediate value.

- **Basic Visual Directory Tree**: A simple, interactive tree structure of the repository's files and folders.
- **Basic Project Overview Card**: A card that displays the project's name and a concise, AI-generated summary of its purpose.

### Medium Efforts

These features provide significant value and require a moderate amount of work to implement.

- **Full Visual Directory Tree**: The complete visual directory tree with all features, including:
  - Proper indentation, folder icons, and file type icons.
  - Hover functionality that shows an AI-generated purpose of the file, a list of functions/classes, file size, programming language, and the number of imports/exports.
  - Color-coded files by type (e.g., components, configs, tests).
  - Special icons to highlight entry points like `index.js` or `main.py`.
- **Full Project Overview Card**: The complete project overview card with all features, including:
  - An AI-generated explanation of the project's purpose.
  - The detected technology stack.
  - "How to run" commands extracted from the README.
  - The main entry point and folder structure type.
- **Smart Search Functionality**: A search bar that allows users to:
  - Search by purpose (e.g., "authentication," "database").
  - Search by file and function name with autocomplete.
  - Filter search results by file type.

### WOW Factors (High Effort)

These are the game-changing features that will make CodeGlance an indispensable tool for developers.

- **File Quick View Panel**: A detailed panel that appears when a user clicks on a file, showing:
  - A list of functions with AI-generated descriptions.
  - The file's dependencies and dependents.
  - A complexity indicator (Simple/Medium/Complex).
  - Key variables and constants.
- **Code Flow Visualizer**: A visual flowchart that maps out the project's architecture, including:
  - The starting point of the application.
  - Major components and modules.
  - Connections and data flow between different parts of the codebase.
- **AI Explainer Sidebar**: A context-aware sidebar that can:
  - Explain the purpose and functionality of a file.
  - Show how a file connects to other parts of the codebase.
  - Suggest where to look next for guided exploration.
  - Identify and explain design patterns used in the code.

## Technology Stack

- **Frontend**: Next.js 15, React, TypeScript, Tailwind CSS v4
- **Backend**: Next.js API Routes
- **AI**: Gemini API
- **Platform**: Vercel

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

## Future Vision

The long-term goal is to make CodeGlance an indispensable tool for developers, enabling them to contribute to new projects faster and with more confidence. Future features may include real-time collaboration, integration with IDEs, and support for more programming languages and frameworks.
