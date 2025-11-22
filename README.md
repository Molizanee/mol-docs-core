# user-payment-service

## Getting started

```bash
bun install
cp .env.example .env # populate secrets afterwards
```

Development server:

```bash
bun run api/index.ts
```

## Database & Drizzle ORM

- Environment: set either `DATABASE_URL`/`POSTGRESQL_DATABASE_URL` or the Postgres pieces (`POSTGRESQL_HOST`, `POSTGRESQL_USER`, `POSTGRESQL_PASSWORD`, `POSTGRESQL_DATABASE`). Optional knobs: `POSTGRES_MAX_CONNECTIONS`, `POSTGRES_DISABLE_SSL`.
- Client: `api/db/client.ts` exposes a singleton Drizzle client backed by `postgres` and preloaded schema exports inside `api/db/*.db.schema.ts`.
- CLI config: `drizzle.config.ts` points Drizzle Kit at the schema files and reuses the validated env config.

Common workflows:

```bash
# Re-generate SQL migrations after schema edits
bun run drizzle:generate

# Apply migrations to the target database
bun run drizzle:migrate

# Open Drizzle Studio for quick inspection
bun run drizzle:studio

# Run (or customize) database seeders
bun run db:seed
```

Documented migrations live under `drizzle/` (generated on demand). Commit both the schema changes and the resulting SQL so CI/CD can stay deterministic.
# mol-drive-users-payments-files-services
