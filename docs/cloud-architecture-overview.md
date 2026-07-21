# Cloud Architecture Overview

## System Context

The current application is a local full-stack JavaScript monorepo. No cloud provider, managed service, or deployment topology is defined.

```mermaid
flowchart LR
    user[Todo App User]

    subgraph frontend[packages/frontend]
        react[React Web Application]
    end

    subgraph backend[packages/backend]
        api[Node.js and Express Task API]
        database[(In-Memory SQLite Task Database)]
    end

    user -->|Uses in browser| react
    react -->|HTTPS requests to /api/tasks| api
    api -->|Reads and writes tasks| database
```

## Create a TODO

```mermaid
sequenceDiagram
    actor User as Todo App User
    participant UI as React Web Application
    participant API as Express Task API
    participant DB as In-Memory SQLite Task Database

    User->>UI: Enter task details and submit
    UI->>API: POST /api/tasks
    API->>API: Validate task title
    API->>DB: Insert task record
    DB-->>API: Return created task
    API-->>UI: 201 Created with task data
    UI-->>User: Display the new task
```