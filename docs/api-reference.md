# API Reference

All endpoints require authentication via Bearer token.

## Base URL

```
https://api.testzeus.dev/v1
```

## Authentication

Include your API key in the `Authorization` header:

```
Authorization: Bearer tk_live_abc123
```

## Endpoints

### GET /status

Returns server health status.

**Response:**

```json
{
  "status": "ok",
  "version": "1.2.0",
  "uptime": 84600
}
```

### GET /projects

List all projects for the authenticated user.

**Query Parameters:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `page` | integer | 1 | Page number |
| `limit` | integer | 20 | Items per page (max 100) |
| `sort` | string | `created_at` | Sort field |

**Response:**

```json
{
  "data": [
    {
      "id": "proj_001",
      "name": "My Project",
      "created_at": "2026-01-15T10:30:00Z",
      "status": "active"
    }
  ],
  "meta": {
    "page": 1,
    "total": 42
  }
}
```

### POST /projects

Create a new project.

**Request Body:**

```json
{
  "name": "New Project",
  "description": "A test project"
}
```

**Response:** `201 Created`

### DELETE /projects/:id

Delete a project by ID.

**Response:** `204 No Content`

## Error Codes

| Code | Meaning |
|------|---------|
| 400 | Invalid request body |
| 401 | Missing or invalid API key |
| 404 | Resource not found |
| 429 | Rate limit exceeded (100 req/min) |
| 500 | Internal server error |

## Rate Limits

- **Free tier**: 100 requests/minute
- **Pro tier**: 1,000 requests/minute
- **Enterprise**: Custom limits
