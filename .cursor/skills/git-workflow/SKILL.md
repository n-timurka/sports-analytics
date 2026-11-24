---
name: git-workflow
description: Branching, worktrees, conventional commits, and pull-request creation for the multi-agent workflow. Use for any git or GitHub PR operation.
---

# Git Workflow Skill

## Branching

```bash
git checkout -b feature/123-short-description
# or with worktree
git worktree add ../wt-feature-123 -b feature/123-short-description
```

## Commits

Use Conventional Commits. Always reference the issue.

```bash
git commit -m "feat(web): add standings table

Closes #123"
```

## Pull requests

Use `gh pr create` with a body that includes Summary, Implementation, Test plan, and the issue reference.

Never force-push shared branches. Never merge.
