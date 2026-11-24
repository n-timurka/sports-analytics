# Sports Analytics — Multi-Agent Cursor Setup

Ready-to-use AI instruction pack for developing the sports analytics platform with Cursor + Grok models, tightly integrated with GitHub issues and the 11-step workflow.

## What is included

```
.
├── AGENTS.md                          # Root agent instructions (always read)
├── agents/                            # Role definitions
│   ├── planner.md
│   ├── nuxt-dev.md
│   ├── python-dev.md
│   ├── qa.md
│   ├── git.md
│   ├── ci-cd.md
│   ├── reviewer.md
│   └── documentation.md
├── .cursor/
│   ├── rules/                         # Cursor project rules (.mdc)
│   │   ├── 00-core.mdc
│   │   ├── nuxt.mdc
│   │   ├── python.mdc
│   │   └── review.mdc
│   └── skills/                        # On-demand skills
│       ├── github-issues/
│       ├── nuxt-supabase/
│       ├── python-parser/
│       ├── testing-qa/
│       ├── git-workflow/
│       ├── ci-cd/
│       ├── code-review/
│       └── documentation/
└── docs/
    └── MULTI_AGENT_WORKFLOW.md
```

## Installation

Copy everything into the **root** of your sports-analytics repository:

```bash
cp -r AGENTS.md agents .cursor docs /path/to/your/repo/
```

Or merge selectively if you already have some of these files.

## How to use

In Cursor Agent chat:

```
@planner Work on issue #123
```

The Planner will:

1. Fetch the issue
2. Create a plan
3. Delegate to the right specialists
4. Drive the loop until a PR is opened and the issue is updated

You stay in control of merges and any product decisions.

## Customisation

- Adjust stack details or folder layout in `AGENTS.md`.
- Tighten or relax review severity in `agents/reviewer.md`.
- Add new skills under `.cursor/skills/<name>/SKILL.md` following the existing format.
- Add path-scoped rules as new `.mdc` files under `.cursor/rules/`.

## Requirements

- Cursor (with Grok models available)
- GitHub CLI (`gh`) authenticated, or GitHub MCP configured
- Project already using (or ready for) Nuxt + Supabase + Python parser layout described in `AGENTS.md`
