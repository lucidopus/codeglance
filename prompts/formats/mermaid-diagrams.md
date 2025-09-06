# CodeGlance Mermaid Diagrams Output Prompt

You are generating interactive diagrams using Mermaid syntax to visualize architecture, flows, and relationships.

## Input Repository
Analyze the repository at: [REPOSITORY_PATH]

## Mermaid Diagram Types to Generate

### 1. Architecture Diagram
```mermaid
graph TB
    subgraph "Frontend"
        UI[React App]
        State[Redux Store]
    end
    
    subgraph "Backend"
        API[REST API]
        Auth[Auth Service]
        DB[(PostgreSQL)]
    end
    
    UI --> State
    State --> API
    API --> Auth
    API --> DB
    
    style UI fill:#61dafb
    style API fill:#68a063
    style DB fill:#336791
```

### 2. Sequence Diagrams
```mermaid
sequenceDiagram
    participant User
    participant Frontend
    participant API
    participant Database
    
    User->>Frontend: Login Request
    Frontend->>API: POST /auth/login
    API->>Database: Verify Credentials
    Database-->>API: User Data
    API-->>Frontend: JWT Token
    Frontend-->>User: Dashboard View
```

### 3. Class Diagrams
```mermaid
classDiagram
    class User {
        +String id
        +String email
        +String name
        +login()
        +logout()
    }
    
    class Post {
        +String id
        +String title
        +String content
        +publish()
        +archive()
    }
    
    User "1" --> "*" Post : creates
```

### 4. Entity Relationship
```mermaid
erDiagram
    USER ||--o{ POST : creates
    USER ||--o{ COMMENT : writes
    POST ||--o{ COMMENT : has
    POST ||--o{ TAG : tagged
    
    USER {
        string id PK
        string email UK
        string username
        datetime created_at
    }
    
    POST {
        string id PK
        string user_id FK
        string title
        text content
    }
```

### 5. State Diagrams
```mermaid
stateDiagram-v2
    [*] --> Draft
    Draft --> UnderReview : Submit
    UnderReview --> Approved : Approve
    UnderReview --> Rejected : Reject
    Rejected --> Draft : Revise
    Approved --> Published : Publish
    Published --> Archived : Archive
    Archived --> [*]
```

### 6. Flowcharts
```mermaid
flowchart TD
    Start([User Visits Site])
    Auth{Authenticated?}
    Login[Login Page]
    Dashboard[Dashboard]
    Public[Public Page]
    
    Start --> Auth
    Auth -->|Yes| Dashboard
    Auth -->|No| Login
    Login --> Auth
    Auth -->|Guest| Public
```

### 7. Git Graph
```mermaid
gitGraph
    commit
    branch feature
    checkout feature
    commit
    commit
    checkout main
    merge feature
    commit
    branch hotfix
    checkout hotfix
    commit
    checkout main
    merge hotfix
```

### 8. Gantt Chart (for roadmap)
```mermaid
gantt
    title Development Roadmap
    dateFormat YYYY-MM-DD
    
    section Phase 1
    Setup           :2024-01-01, 7d
    Core Features   :7d
    
    section Phase 2
    API Development :2024-01-15, 14d
    Testing         :7d
```

### 9. Pie Chart (for metrics)
```mermaid
pie title Code Distribution
    "JavaScript" : 45
    "TypeScript" : 30
    "CSS" : 15
    "HTML" : 10
```

### 10. Journey Map
```mermaid
journey
    title User Onboarding Journey
    section Sign Up
      Visit Landing: 5: User
      Create Account: 3: User
      Verify Email: 2: User
    section First Use
      Login: 5: User
      Tutorial: 4: User
      First Action: 3: User
    section Regular Use
      Daily Login: 5: User
      Use Features: 4: User
```

## Output Structure

Generate `guide/diagrams.md` containing:

### 1. System Overview
Large architecture diagram showing all components

### 2. Data Flow
Sequence diagrams for main user flows

### 3. Database Schema
ER diagram of database structure

### 4. Component Relationships
Class/component diagrams

### 5. State Management
State diagrams for complex workflows

### 6. Deployment Architecture
Flowchart of deployment pipeline

## Diagram Guidelines
- Keep diagrams readable (not too complex)
- Use consistent colors for same types
- Add titles and descriptions
- Link diagrams to relevant documentation
- Provide both high-level and detailed views

Generate Mermaid diagram documentation for [REPOSITORY_PATH] now.