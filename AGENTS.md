# AGENTS.md

Guidance for AI coding agents working in this repository.

## Project

GoBarber: barbershop appointment scheduling platform as a monorepo, built
during the Rocketseat GoStack bootcamp. Legacy project with era-pinned
dependencies (2020-2021): React 17 / CRA 4, TypeScript 4.1, TypeORM 0.2,
Express 4.

- `apps/frontend`: React SPA (auth, booking calendar, provider dashboard)
- `apps/backend`: Node/TypeScript REST API (JWT auth, appointments, uploads, notifications)

## Commands

Backend:

```bash
cd apps/backend
yarn install
cp .env.example .env        # requires PostgreSQL, MongoDB and Redis running
yarn typeorm migration:run
yarn dev:server             # http://localhost:3333
yarn test                   # Jest unit tests
```

Frontend:

```bash
cd apps/frontend
yarn install
yarn start                  # http://localhost:3000, expects API on 3333
```

## Structure (backend)

Modular DDD layout under `apps/backend/src`:

- `modules/appointments`: appointments and providers domain (services, infra/typeorm, infra/http routes)
- `modules/users`: users, sessions, password recovery, profile
- `shared/infra/http/server.ts`: HTTP entry point
- `shared/infra/typeorm`: database connection and migrations
- Dependency injection via tsyringe, validation via celebrate, uploads via multer (S3 or disk)

Frontend follows standard CRA structure (`pages`, `components`, `hooks`, `services`) under `apps/frontend/src`.

## Branches

- `main`: primary branch
- `develop`: integration branch

## Rules for agents

- Docs-only maintenance phase: no dependency upgrades, no runtime behavior changes
- Never commit `.env`; only `.env.example` templates are tracked
