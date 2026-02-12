# Getting Started

Welcome to TestZeus. This guide covers setup and basic usage.

## Prerequisites

- Node.js 20+
- PostgreSQL 15+
- A GitHub account

## Installation

```bash
git clone https://github.com/zedzcodez/testzeus.git
cd testzeus
npm install
```

## Configuration

Create a `.env` file with the following variables:

```env
DATABASE_URL=postgresql://localhost:5432/testzeus
API_KEY=your-api-key-here
PORT=3000
```

## Running Locally

```bash
npm run dev
```

The server starts at `http://localhost:3000`.

## First Steps

1. Create an account at `/signup`
2. Generate an API key in Settings
3. Make your first API call:

```bash
curl -H "Authorization: Bearer YOUR_KEY" http://localhost:3000/api/status
```

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Port already in use | Change `PORT` in `.env` |
| Database connection failed | Verify PostgreSQL is running |
| Auth errors | Regenerate your API key |

## Next Steps

- Read the [API Reference](api-reference.md)
- Review the [Architecture](architecture.md)
