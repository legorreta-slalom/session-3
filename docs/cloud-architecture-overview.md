# Cloud Architecture Overview

This monorepo contains a React frontend, an Express API, and an in-memory SQLite store used by the backend during runtime.

```mermaid
flowchart LR
    user[User Browser]
    frontend[React Frontend\npackages/frontend]
    api[Express API\npackages/backend]
    store[(In-Memory SQLite Store)]

    user --> frontend
    frontend -->|HTTP /api/tasks| api
    api --> store
```

## Create TODO Sequence

```mermaid
sequenceDiagram
    actor User
    participant Frontend as React Frontend
    participant API as Express API
    participant Store as In-Memory SQLite Store

    User->>Frontend: Enter task details and submit form
    Frontend->>+API: POST /api/tasks
    Note over Frontend,API: Request includes the new TODO payload
    API->>+Store: Insert TODO record
    Store-->>-API: Created TODO record
    API-->>-Frontend: 201 Created with TODO JSON
    Frontend-->>User: Render the new TODO in the list
```

## Notes

- The browser loads the React application from the frontend package.
- The React app sends task requests to the Express API.
- The Express API reads from and writes to an in-memory SQLite database.
- The in-memory store is reset when the backend process restarts.