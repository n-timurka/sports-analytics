# Sports Analytics Platform — Agent Instructions

You are working on a **local-first sports analytics platform** (football + basketball).

## Stack (non-negotiable)

| Layer | Technology |
|-------|------------|
| Frontend | Nuxt 3/4 + Vue 3 + TypeScript |
| Data access | Supabase JS client + optional pg_graphql (no custom backend API for CRUD) |
| Database | Postgres (local Docker / Supabase managed) |
| Data parser / ETL | Python (preferred) or Rust |
| Local runtime | Docker Compose |
| Production | Vercel (Nuxt) + Supabase |
| Package manager | pnpm (never npm/yarn for Node parts) |

## Project layout

```
sports-analytics/
├── apps/web/                 # Nuxt application
├── packages/db/              # shared types, migrations, schema
├── services/parser/          # Python ETL / data ingestion
├── supabase/                 # Supabase config + migrations
├── docker/                   # docker-compose and related
├── .github/workflows/        # CI/CD
└── AGENTS.md                 # this file
```

## Core principles

1. Prefer PostgREST (`.from().select()`) and Postgres functions/RPCs over custom API routes.
2. Use Row Level Security (RLS) from day one.
3. Keep components under ~200 lines. Extract composables and pure functions.
4. Never invent requirements. If an issue is unclear, ask clarifying questions.
5. Every change must be testable. Prefer tests next to code or in co-located `__tests__`.
6. Commit messages follow Conventional Commits (`feat:`, `fix:`, `docs:`, `test:`, `ci:`, `chore:`).
7. Branch naming: `feature/<issue-number>-short-description` or `fix/<issue-number>-short-description`.

## Multi-agent workflow (mandatory)

When the user asks to work on a GitHub issue or starts a feature, follow this exact sequence. The **Planner** is the orchestrator.

1. **Issue selection** — Planner fetches the issue (title, body, labels, comments, acceptance criteria).
2. **Analysis and planning** — Planner analyses the codebase, identifies required skills/agents, and breaks work into subtasks. If requirements are unclear → ask questions; do not invent.
3. **Git preparation** — Git agent creates the branch.
4. **Implementation** — nuxt-dev and/or python-dev implement. Prefer separate Git worktrees when multiple developers run in parallel.
5. **QA** — QA agent writes and runs tests. Defects go back to the orchestrator.
6. **Documentation** — Documentation agent updates README, technical docs, changelog, version info as needed.
7. **CI/CD** — CI/CD agent verifies/updates GitHub Actions quality gates.
8. **Independent review** — Reviewer (different model from the developer) examines the full diff. Findings: critical / major / minor / informational.
9. **Fix and re-review** — Planner routes actionable findings. QA + Reviewer re-run as needed.
10. **Pull request** — Git agent commits, pushes, opens PR with summary, issue reference, implementation notes, and test results.
11. **Final status** — Planner updates the GitHub issue (comment + status). **Never auto-merge.**

## Agent roster

| Agent | Role | Primary skills |
|-------|------|----------------|
| **planner** | Orchestrator, issue analysis, task breakdown, status updates | github-issues |
| **nuxt-dev** | Frontend / Nuxt / Supabase client work | nuxt-supabase |
| **python-dev** | Data parser, ETL, analytics scripts | python-parser |
| **qa** | Tests, coverage, defect reporting | testing-qa |
| **git** | Branches, commits, PRs, worktrees | git-workflow |
| **ci-cd** | GitHub Actions, quality gates | ci-cd |
| **reviewer** | Independent code review | code-review |
| **documentation** | README, docs, changelog | documentation |

## How to invoke

- Start with: `@planner Work on issue #123` or `Start feature from GitHub issue #123`.
- Planner will delegate using the format: `Delegate to <agent>: <clear task + acceptance criteria + allowed paths>`.
- Each specialist agent must stay inside its allowed paths and report completion (or blockers) back to the planner.

## Commands (quick reference)

```bash
# Local
pnpm --filter web dev
docker compose up -d
npx supabase start

# Tests
pnpm --filter web test
cd services/parser && pytest

# Quality
pnpm lint && pnpm typecheck
```

## Definition of Done (every issue)

- [ ] Acceptance criteria from the issue are met
- [ ] Tests written and passing
- [ ] Types / lint clean
- [ ] Docs / changelog updated when user-facing
- [ ] PR opened with issue link
- [ ] Issue commented and status updated
- [ ] No critical or major open review findings
