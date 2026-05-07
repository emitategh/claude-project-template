# Claude Project Template

A conventions-only project template for Claude Code projects. Stack-agnostic.

## What's included

```
├── CLAUDE.md                        ← fill in: project overview, stack, commands
├── CLAUDE.local.md.example          ← copy to CLAUDE.local.md for local overrides
├── .gitignore                       ← ignores plans/, secrets, plugin cache
├── .claude/
│   ├── settings.json                ← base permissions (extend as needed)
│   └── rules/
│       └── git-workflow.md          ← branching, commits, PRs, merge strategy
└── docs/
    └── superpowers/
        └── specs/                   ← commit design decisions and architecture here
```

## What's NOT included (by design)

- `docs/superpowers/plans/` — gitignored. Implementation plans are ephemeral.
- Stack scaffold — this template is stack-agnostic.

## How to use

### As a GitHub template
1. Click **Use this template** on GitHub
2. Clone your new repo
3. Fill in `CLAUDE.md` with your project details
4. Add stack-specific rules to `.claude/rules/` as needed
5. Start brainstorming with Claude Code

### Manually
```bash
cp -r claude-project-template my-new-project
cd my-new-project
git init
git add .
git commit -m "chore: init project from template"
```

## Planning workflow (with Claude Code superpowers)

1. **Brainstorm** — `/brainstorming` to go from idea to approved spec
2. **Plan** — `/writing-plans` to generate a task-by-task implementation plan
3. **Execute** — one branch per task, one PR per task, squash and merge
4. **Decisions** → `docs/superpowers/specs/` (committed)
5. **Plans** → `docs/superpowers/plans/` (gitignored, ephemeral)
