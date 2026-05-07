# Git Workflow Rules

## Branching Strategy

**Simple:** `main` is always production-ready. All work happens on short-lived branches that merge back to `main`.

Branch types:
- `feat/` — new features
- `fix/` — bug fixes
- `chore/` — tooling, config, dependencies, infrastructure
- `docs/` — documentation only
- `refactor/` — code restructuring with no behavior change
- `test/` — tests only

## Branch Naming

```
type/task-N-short-description
```

Examples:
- `feat/task-3-firebase-auth`
- `feat/task-9-chat-system`
- `fix/task-9-message-count-off-by-one`
- `chore/task-1-docker-scaffold`

## Commit Messages — Conventional Commits

```
type(scope): short description

Optional body explaining WHY, not WHAT.
```

Types: `feat`, `fix`, `chore`, `docs`, `refactor`, `test`, `perf`

Examples:
```
feat(auth): add Firebase Admin token verification
fix(chat): correct message count enforcement on free tier
chore(docker): add postgres healthcheck to compose
test(extraction): add structured profile extraction tests
```

Rules:
- Subject line: imperative mood, max 72 chars, no period at end
- Scope: optional, use the system name (e.g. `auth`, `chat`, `billing`)
- Body: only when the WHY is non-obvious

## Pull Requests

- **One PR per implementation plan task**
- PRs touch only what the task requires — no opportunistic cleanup in unrelated files
- Title follows Conventional Commits format: `feat(auth): Firebase auth with Google + email`
- PR description: what changed + how to test locally
- Self-review before marking ready: run tests, check diff for accidental files

## Merge Strategy

**Squash and merge.** All commits in the branch become one commit on `main`. The squash message follows Conventional Commits format.

## File Tracking

**Committed to git:**
- `CLAUDE.md` — project overview and key decisions
- `.claude/rules/` — coding conventions
- `.claude/settings.json` — permissions and hooks
- `docs/superpowers/specs/` — architecture and design decision records

**Gitignored:**
- `docs/superpowers/plans/` — implementation plans are ephemeral once executed
- `.claude/plugins/` — downloaded plugin/skill cache
- All secrets and local overrides

## Protected Rules

- Never commit directly to `main`
- Never commit secrets (`.env`, `firebase-service-account.json`, etc.)
- Never force-push `main`
- Delete branch after merge
- A branch should not outlive its task — if it grows beyond one task, split it
