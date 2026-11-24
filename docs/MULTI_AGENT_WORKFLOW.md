# Multi-Agent Development Workflow

This project uses a structured multi-agent process driven by Cursor (Grok models recommended).

## Quick start in Cursor

1. Copy the contents of this folder into the root of your sports-analytics repository (or merge the directories).
2. Ensure `AGENTS.md` is at the repo root.
3. Open the project in Cursor.
4. Start a conversation with:

```
@planner Work on GitHub issue #42
```

or

```
Start the multi-agent workflow for issue #42. Follow AGENTS.md.
```

## Agent map

| Agent            | File                    | Responsibility                          |
|------------------|-------------------------|-----------------------------------------|
| planner          | agents/planner.md       | Orchestration, planning, status         |
| nuxt-dev         | agents/nuxt-dev.md      | Nuxt / Supabase frontend                |
| python-dev       | agents/python-dev.md    | Data parser / ETL                       |
| qa               | agents/qa.md            | Tests and defect reports                |
| git              | agents/git.md           | Branches, commits, PRs, worktrees       |
| ci-cd            | agents/ci-cd.md         | GitHub Actions quality gates            |
| reviewer         | agents/reviewer.md      | Independent review (prefer other model) |
| documentation    | agents/documentation.md | README, docs, changelog                 |

## Skills

Located under `.cursor/skills/`:

- github-issues
- nuxt-supabase
- python-parser
- testing-qa
- git-workflow
- ci-cd
- code-review
- documentation

## Recommended model usage

- **Planner / Reviewer**: Grok 4.7 or strongest available reasoning model
- **nuxt-dev / python-dev**: Grok Code or Grok 4.5 / 4.7
- **QA / Git / Docs / CI**: any capable model; consistency matters more than peak intelligence

For true independence, run the Reviewer in a separate chat or with a different model than the implementer.

## GitHub integration

The workflow expects the `gh` CLI (authenticated) or a GitHub MCP server so agents can:

- read issues and comments
- create branches and PRs
- comment on issues

Without GitHub access the Planner will ask you to paste the issue content.

## Parallelism

When both frontend and parser work is required, the Planner should:

1. Ask the Git agent to create worktrees (or separate branches).
2. Delegate to nuxt-dev and python-dev with non-overlapping paths.
3. Merge the results carefully before review.
