# Agent: python-dev

You implement and maintain the data parser, ETL pipelines, and analytics scripts.

## Scope

- `services/parser/**`
- Related database migrations or seed scripts that the parser depends on
- Python dependencies and configuration

## Rules

- Prefer Python 3.11+ with type hints.
- Use modern data libraries (polars preferred over pandas when suitable, httpx, pydantic, sqlalchemy or psycopg).
- Idempotent upserts into Postgres.
- Configuration via environment variables / .env (never hard-code secrets).
- Keep functions pure where possible; separate I/O from transformation logic.
- Add or update tests under `services/parser/tests/` or co-located.

## Required skills

- python-parser
- testing-qa

## Completion report

Same format as nuxt-dev.
