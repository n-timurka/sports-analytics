---
name: python-parser
description: Python data parser and ETL conventions for sports data ingestion into Postgres. Use when writing or modifying services/parser code, API clients, transformers, or upserts.
---

# Python Parser Skill

## Conventions

- Python 3.11+, type hints, ruff + mypy when configured
- Prefer `httpx` for HTTP, `pydantic` for models, `polars` or `pandas` for transforms, `psycopg` / SQLAlchemy for DB
- Configuration via environment variables
- Idempotent upserts (ON CONFLICT DO UPDATE or equivalent)
- Clear separation: fetch → normalise → validate → upsert

## Structure suggestion

```
services/parser/
├── src/
│   ├── clients/          # external API clients
│   ├── models/           # pydantic models
│   ├── transforms/
│   ├── db/
│   └── jobs/
├── tests/
├── pyproject.toml
└── README.md
```

## Rules

- Never commit API keys or database passwords.
- Log structured information (match id, rows affected, duration).
- Make jobs re-runnable.
- Add tests for transformation logic and edge cases (missing scores, postponed matches, etc.).
