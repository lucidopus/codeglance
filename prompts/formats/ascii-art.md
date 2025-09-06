# CodeGlance ASCII Art Output Prompt

You are generating terminal-friendly ASCII art documentation for developers who prefer text-based visualizations.

## Input Repository
Analyze the repository at: [REPOSITORY_PATH]

## ASCII Art Visualization Types

### 1. Directory Trees
```
project/
├── src/
│   ├── components/        # UI Components
│   │   ├── Button.jsx     # Reusable button
│   │   └── Card.jsx       # Card container
│   ├── services/          # Business logic
│   │   ├── api.js         # API client
│   │   └── auth.js        # Authentication
│   └── utils/             # Helpers
│       └── format.js      # Formatters
├── tests/                 # Test files
└── docs/                  # Documentation
```

### 2. Architecture Diagrams
```
┌─────────────────────────────────────────────┐
│                  Frontend                    │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  │
│  │   React  │  │  Redux   │  │  Router  │  │
│  └─────┬────┘  └─────┬────┘  └─────┬────┘  │
│        └──────────────┼──────────────┘      │
└────────────────────────┬────────────────────┘
                         │
                    HTTP │ REST
                         ↓
┌─────────────────────────────────────────────┐
│                   Backend                    │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  │
│  │  Express │←→│   Auth   │←→│ Database │  │
│  └──────────┘  └──────────┘  └──────────┘  │
└─────────────────────────────────────────────┘
```

### 3. Flow Diagrams
```
    [User Input]
         │
         ↓
    ╔═══════════╗
    ║ Validate  ║
    ╚═══════════╝
         │
    Valid? ──No──→ [Error Message]
         │
        Yes
         ↓
    ╔═══════════╗
    ║  Process  ║
    ╚═══════════╝
         │
         ↓
    [Save to DB]
         │
         ↓
    [Return Success]
```

### 4. Component Relationships
```
     ┌────────┐
     │  App   │
     └───┬────┘
         │
    ┌────┴────┬────────┬────────┐
    ↓         ↓        ↓        ↓
┌────────┐ ┌──────┐ ┌──────┐ ┌──────┐
│ Header │ │ Main │ │ Side │ │Footer│
└────────┘ └──┬───┘ └──────┘ └──────┘
              │
        ┌─────┴─────┬─────────┐
        ↓           ↓         ↓
   ┌────────┐  ┌────────┐ ┌────────┐
   │ List   │  │ Detail │ │ Form   │
   └────────┘  └────────┘ └────────┘
```

### 5. Database Schema
```
┌──────────────┐     ┌──────────────┐
│    users     │     │    posts     │
├──────────────┤     ├──────────────┤
│ id        PK │←───┐│ id        PK │
│ email     UQ │    ││ user_id   FK │
│ username     │    └│ title        │
│ created_at   │     │ content      │
└──────────────┘     │ created_at   │
                     └──────────────┘
                            ↓ 1:N
                     ┌──────────────┐
                     │   comments   │
                     ├──────────────┤
                     │ id        PK │
                     │ post_id   FK │
                     │ user_id   FK │
                     │ content      │
                     └──────────────┘
```

### 6. Timeline/Process
```
Start        Analysis       Design        Build         Test         Deploy
  │             │             │            │             │             │
  ●─────────────●─────────────●────────────●─────────────●─────────────●
  │                                                                     │
  └─────────────────────────── 6 weeks ────────────────────────────────┘
        Week 1       Week 2      Week 3-4      Week 5       Week 6
```

### 7. API Endpoints
```
API Routes
│
├── /auth
│   ├── POST   /login     ← Authenticate user
│   ├── POST   /logout    ← End session
│   └── POST   /refresh   ← Refresh token
│
├── /users
│   ├── GET    /          ← List all users
│   ├── GET    /:id       ← Get specific user
│   ├── POST   /          ← Create user
│   ├── PUT    /:id       ← Update user
│   └── DELETE /:id       ← Delete user
│
└── /posts
    ├── GET    /          ← List posts
    └── POST   /          ← Create post
```

### 8. State Machine
```
     ┌─────────┐
     │  IDLE   │
     └────┬────┘
          │ start
          ↓
     ┌─────────┐
  ┌→ │ LOADING │
  │  └────┬────┘
  │       │ success
  │       ↓
  │  ┌─────────┐
  │  │ SUCCESS │
  │  └─────────┘
  │ 
  └── error ←┘
     ↓
  ┌─────────┐
  │  ERROR  │
  └─────────┘
```

### 9. Metrics Display
```
Code Coverage Report
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
File            │ Coverage │ Lines
────────────────┼──────────┼─────────────
src/index.js    │ ████░░░░ │  87% (94/108)
src/auth.js     │ ███████░ │  95% (57/60)
src/utils.js    │ ██████░░ │  78% (39/50)
────────────────┼──────────┼─────────────
Total           │ ████░░░░ │  86% (190/218)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### 10. Box Diagrams
```
╔══════════════════════════════════════╗
║          Application Name            ║
╠══════════════════════════════════════╣
║                                      ║
║  ┌────────────┐    ┌────────────┐   ║
║  │  Module A  │───→│  Module B  │   ║
║  └────────────┘    └────────────┘   ║
║         ↓                ↓          ║
║  ┌────────────┐    ┌────────────┐   ║
║  │  Module C  │←───│  Module D  │   ║
║  └────────────┘    └────────────┘   ║
║                                      ║
╚══════════════════════════════════════╝
```

## Output Guidelines

### Character Set
- Use standard ASCII characters
- Avoid Unicode unless necessary
- Ensure compatibility with all terminals

### Layout Rules
- Maximum width: 80 characters
- Use consistent box drawing characters
- Align elements properly
- Add legends where needed

### Visual Hierarchy
```
═══ Double lines for main containers
─── Single lines for subdivisions
··· Dotted lines for optional/weak connections
→ ← ↑ ↓ Arrows for flow direction
● ○ □ ■ Markers for states/points
```

## Output Structure

Generate `guide/ascii-diagrams.md` containing:
1. Project structure tree
2. Architecture overview
3. Data flow diagrams
4. Component hierarchy
5. API structure
6. Database schema
7. Deployment flow

Each diagram should include:
- Title
- Brief description
- Legend (if needed)
- Related documentation links

Generate ASCII art documentation for [REPOSITORY_PATH] now.