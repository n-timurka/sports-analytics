---
name: github-issues
description: Fetch, analyse, comment on, and update GitHub issues and projects. Use when selecting work, reading acceptance criteria, posting status, or linking PRs to issues.
---

# GitHub Issues Skill

## Capabilities

- Read issue title, body, labels, milestone, assignees, comments, and linked PRs.
- Extract acceptance criteria (look for checklists, "AC:", "Acceptance Criteria", or Given/When/Then).
- Post comments and update issue state (open/closed) or project status fields when the GitHub CLI or API is available.
- Reference issues correctly in commits and PRs (`Closes #N`, `Refs #N`).

## Preferred tools

- `gh issue view <number> --comments`
- `gh issue list --label ...`
- `gh issue comment <number> --body "..."`
- `gh pr create ...`
- GitHub MCP / API if configured in the environment

## Rules

- Never invent acceptance criteria. Quote or paraphrase what is written; if missing, ask.
- Always include the issue number in branch names, commit footers, and PR titles/bodies.
- Final status comment should summarise what was delivered and link the PR.
- Do not auto-merge.
