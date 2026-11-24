---
name: ci-cd
description: GitHub Actions workflows and quality gates. Use when inspecting or updating CI for lint, typecheck, tests, and build.
---

# CI/CD Skill

## Expectations

Every PR should run at minimum:

- Lint
- Typecheck
- Unit tests (web + parser)
- Build (web)

## Implementation notes

- Cache pnpm store
- Use `pnpm` exclusively
- Keep jobs focused; split only when needed for speed or isolation
- Database-dependent jobs should use services or Supabase local when practical
