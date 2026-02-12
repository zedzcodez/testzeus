# Architecture

## Overview

TestZeus follows a layered architecture with clear separation of concerns.

```
+---------------------------------+
|         Client (React)          |
+---------------------------------+
|       API Gateway (Next.js)     |
+---------------------------------+
|      Service Layer (Node.js)    |
+---------------------------------+
|     Data Layer (PostgreSQL)     |
+---------------------------------+
```

## Components

### API Gateway

- Routes incoming requests
- Handles authentication and rate limiting
- Request validation via Zod schemas

### Service Layer

Core business logic organized into services:

- **ProjectService** — CRUD for projects
- **DocumentService** — Document management and sync
- **AuthService** — Token generation and validation
- **WebhookService** — GitHub webhook processing

### Data Layer

PostgreSQL with Row Level Security (RLS) for multi-tenant isolation.

**Key tables:**

| Table | Purpose |
|-------|---------|
| `users` | User accounts |
| `projects` | Project metadata |
| `documents` | Synced documents |
| `api_keys` | Authentication tokens |
| `webhook_events` | Incoming webhook log |

## Data Flow

1. User pushes to GitHub
2. GitHub fires webhook to `/api/webhooks/github`
3. WebhookService validates signature
4. DocumentService fetches updated files
5. Content stored in `documents` table
6. Search index updated asynchronously
