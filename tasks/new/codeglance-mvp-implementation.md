# CodeGlance MVP Implementation Task

## Project Overview

CodeGlance is a tool that transforms GitHub repositories into intuitive, visual interfaces to help developers quickly understand unfamiliar codebases. Users paste a GitHub repository URL and get a user-friendly exploration interface.

## Task Objective

Implement the core MVP features that enable users to rapidly understand any codebase structure and functionality through visual exploration and AI-powered explanations.

## Current Project State

- Fresh Next.js 15 project with App Router and TypeScript
- Tailwind CSS v4 configured
- Basic project structure in place with default Next.js landing page
- No backend functionality implemented yet
- No GitHub integration exists

## MVP Features to Implement

### 1. Visual Directory Tree
**Purpose**: Primary navigation interface showing repository structure
- Display GitHub repository files/folders in an interactive tree
- Add proper indentation, folder icons, and file type icons
- Implement hover functionality that shows:
  - One-line AI-generated purpose of the file
  - List of functions/classes inside the file
  - File size and programming language
  - Number of imports/exports
- Color code files by type (components=blue, configs=gray, tests=green)
- Highlight entry points (index.js, main.py, app.tsx) with special icons

### 2. Project Overview Card
**Purpose**: Give instant understanding of what the project does
- Display at the top of the interface
- Show AI-generated plain English explanation of project purpose
- Detect and display technology stack (React, Node.js, Python, etc.)
- Extract and display "how to run" commands from README
- Identify and highlight the main entry point file
- Categorize folder structure type (MVC, feature-based, domain-driven)

### 3. File Quick View Panel
**Purpose**: Detailed view when user clicks on any file
- Display function list with AI-generated one-line descriptions
- Show dependencies (what this file imports)
- Show dependents (what files import this one)
- Add complexity indicator (Simple/Medium/Complex)
- List key variables and constants defined in the file
- Make it a sliding panel or modal that doesn't disrupt navigation

### 4. Code Flow Visualizer
**Purpose**: Show how different parts of the codebase connect
- Create simple flowchart showing:
  - Starting point (main/index files)
  - Major components and modules
  - Connection lines showing relationships
  - Data flow direction with arrows
- Make boxes clickable to jump to corresponding files
- Highlight current file path when viewing specific files

### 5. Smart Search Functionality
**Purpose**: Quick navigation and discovery
- Implement search by purpose (keywords like "authentication", "database", "api")
- Add file name search with autocomplete
- Enable function search across the entire codebase
- Add filters by file type (components only, tests only, configs only)
- Show search results with context and relevance

### 6. AI Explainer Sidebar
**Purpose**: Context-aware assistance for understanding code
- "Explain this file" - Generate purpose and functionality description
- "How does this connect?" - Show file relationships and dependencies
- "Where should I look next?" - Provide guided exploration suggestions
- "What's the pattern here?" - Identify and explain design patterns used
- Make it contextual based on currently selected file or component

## Technical Requirements

### Backend Implementation Needed
- GitHub API integration to fetch repository data
- File content parsing and analysis
- AI integration (using Gemini API as specified) for generating explanations
- Caching mechanism for repository data
- Error handling for invalid repositories or API limits

### Frontend Implementation Needed
- Repository URL input form
- Interactive file tree component
- File preview and details panels
- Search functionality with filtering
- Code flow visualization component
- Responsive design for different screen sizes

### Data Flow
1. User enters GitHub repository URL
2. Backend fetches repository structure via GitHub API
3. Backend analyzes files and generates AI explanations
4. Frontend displays visual directory tree
5. User interactions (hover, click, search) trigger additional API calls
6. Real-time updates to UI based on user exploration

## Success Criteria

A junior developer should be able to:
1. Enter any public GitHub repository URL
2. Immediately see and understand the project structure
3. Navigate through files using visual tree interface
4. Get instant explanations by hovering over files
5. Search for specific functionality or file types
6. Follow the code flow visualization to understand architecture
7. Use AI assistance to get contextual explanations

## Key User Experience Goals

- **Speed**: Understanding a new codebase should take minutes, not hours
- **Visual**: Everything should be visual and intuitive, minimal text walls
- **Progressive**: Start with overview, drill down to details as needed
- **Guided**: AI should guide users to important files and patterns
- **Non-overwhelming**: Simple interface that doesn't replicate existing GitHub features

## Files Likely to be Created/Modified

- `src/app/page.tsx` - Main landing page with repository input
- `src/app/repository/[...params]/page.tsx` - Repository exploration interface
- `src/app/api/repository/` - API routes for GitHub integration
- `src/components/` - UI components for file tree, panels, search
- `src/lib/` - Utility functions for GitHub API, AI integration
- `src/types/` - TypeScript interfaces for data structures

## Context and Considerations

- This is the initial MVP - focus on core functionality over polish
- GitHub API has rate limits that need to be handled gracefully
- AI explanations should be concise and helpful, not verbose
- The tool should complement GitHub, not replicate its existing features
- Performance is important - large repositories should load progressively
- Error handling is crucial for edge cases (private repos, large files, API failures)

## Implementation Notes

The current codebase is a clean Next.js 15 setup with TypeScript and Tailwind CSS. The architecture should leverage:
- Next.js API routes for backend functionality
- React components for interactive UI elements
- TypeScript for type safety across the application
- Tailwind CSS for responsive and consistent styling

Focus on creating a smooth, intuitive user experience that makes exploring unfamiliar codebases feel natural and efficient.