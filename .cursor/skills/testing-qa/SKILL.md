---
name: testing-qa
description: Testing strategy and execution for Nuxt frontend and Python parser. Use when writing tests, running suites, or reporting defects.
---

# Testing & QA Skill

## Frontend (apps/web)

- Unit/component: Vitest + Vue Test Utils
- E2E (when present): Playwright
- Co-locate tests or use `__tests__` / `*.spec.ts` as the project already does
- Mock Supabase client in unit tests; prefer integration tests against local Supabase when available

## Parser (services/parser)

- pytest
- Test pure transform functions thoroughly
- Use fixtures for sample API payloads
- Prefer contract tests over heavy live API calls in CI

## Defect handling

Report defects with severity, reproduction, and suggested owner. Do not mark work done while critical/major defects remain open.
