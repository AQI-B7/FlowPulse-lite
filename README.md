# FlowPulse
## @AQI-B7
FlowPulse is a TypeScript monorepo for a multi-channel direct messaging automation platform built for WhatsApp, Instagram, and TikTok workflows. It brings together a backend API, a React frontend, shared validation code, and a PostgreSQL schema layer to manage inboxes, automation flows, broadcasts, contacts, analytics, and compliance tooling in one system.

## Overview

The product is structured around a SaaS-style workflow engine for businesses that need to manage marketing and support conversations across social messaging channels. The core areas of the platform include:

- Unified inbox for conversation management
- Flow-based automation builder
- Broadcast campaign tools
- Contact and segmentation management
- Analytics and reporting dashboards
- Knowledge-base and AI grounding support
- GDPR and consent-related compliance controls

## Architecture

This repository is organized as a pnpm workspace monorepo.

- `artifacts/api-server` — Express API server
- `artifacts/flowpulse` — React + Vite frontend
- `lib/db` — Drizzle ORM and PostgreSQL schema
- `lib/api-zod` — shared validation schemas
- `lib/api-client-react` — API client utilities for the frontend
- `scripts` — repository tooling and project automation

## Tech Stack

- TypeScript
- Node.js 24
- pnpm workspaces
- Express 5
- PostgreSQL
- Drizzle ORM
- React + Vite
- Zod
- JWT-based authentication
- esbuild

## Features

### Messaging & Inbox

- Unified DM inbox across multiple channels
- Conversation tracking and management
- Read/unread state handling for messaging workflows

### Flows

- Visual automation flow creation
- Trigger-based workflow logic
- Action orchestration for messaging use cases

### Broadcasts

- Bulk communication campaigns
- Scheduled broadcasts
- Segmentation-based messaging

### Contacts

- Unified contact records
- Tags, loyalty metadata, and segmentation
- Consent-aware customer data management

### Analytics

- Messaging performance tracking
- Funnel and attribution analysis
- Time-based reporting and engagement metrics

### Compliance

- GDPR-oriented contact and consent management
- Data export and deletion support patterns
- Governance-friendly operational workflows

## Repository Structure

```text
.
├── artifacts/
│   ├── api-server/
│   │   ├── src/
│   │   ├── package.json
│   │   ├── build.mjs
│   │   └── tsconfig.json
│   ├── flowpulse/
│   │   ├── src/
│   │   ├── package.json
│   │   ├── vite.config.ts
│   │   └── tsconfig.json
│   └── mockup-sandbox/
├── lib/
│   ├── api-client-react/
│   ├── api-spec/
│   ├── api-zod/
│   └── db/
│       ├── src/
│       ├── drizzle.config.ts
│       ├── package.json
│       └── tsconfig.json
├── scripts/
│   ├── src/
│   ├── package.json
│   └── tsconfig.json
├── .gitignore
├── .npmrc
├── .replit
├── .replitignore
├── package.json
├── pnpm-lock.yaml
├── pnpm-workspace.yaml
├── replit.md
├── tsconfig.base.json
├── tsconfig.json
└── README.md
```

## Getting Started

### Prerequisites

- Node.js 24+
- pnpm
- PostgreSQL

### Install dependencies

```bash
pnpm install
```

### Required environment variable

```bash
DATABASE_URL=postgresql://user:password@localhost:5432/flowpulse
```

## Development

### Start the API server

```bash
pnpm --filter @workspace/api-server run dev
```

The API server runs on port `8080`.

### Start the frontend

```bash
pnpm --filter @workspace/flowpulse run dev
```

The frontend uses Vite and is configured to proxy `/api/*` requests to the backend.

### Run type checking

```bash
pnpm run typecheck
```

### Build the project

```bash
pnpm run build
```

## Database

The database layer is managed in `lib/db` using Drizzle ORM. The schema is treated as the source of truth for the application data model.

To push schema changes during development:

```bash
pnpm --filter @workspace/db run push
```

## Authentication

Authentication is implemented with JWT tokens. The token is stored in browser local storage under the key:

```text
fp_token
```

The payload includes information such as:

- `userId`
- `tenantId`
- `email`
- `role`

The frontend sends this token as a bearer token using the `Authorization` header for authenticated API requests.

## Notes

- The project intentionally avoids Supabase and uses a custom Express backend instead.
- Frontend API access is abstracted through local API client modules to keep backend integration clean.
- Vite is used to proxy `/api` requests locally to avoid CORS issues during development.
- The codebase is structured as a scalable monorepo for long-term SaaS growth.

## Scripts

Useful project commands include:

```bash
pnpm run typecheck
pnpm run build
pnpm --filter @workspace/api-server run dev
pnpm --filter @workspace/flowpulse run dev
pnpm --filter @workspace/db run push
```

## License

This repository does not currently declare a project license in its metadata.

## Status

FlowPulse is an active TypeScript-based product codebase with a working backend, frontend, and database foundation for a social DM automation SaaS platform.

