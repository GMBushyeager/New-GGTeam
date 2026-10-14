# GG Team

In-house rebuild of the GG Team trainer assessment app, replacing the
Resourcifi-built app. One Expo codebase ships to iOS and Android, backed by a Node
API on AWS. MongoDB is the operational store and feeds Snowflake downstream.

**Start with [`CLAUDE.md`](CLAUDE.md).** It holds the project rules for people and
for Claude Code. Claude Code reads it automatically at the start of every session.

## Who does what

| Person | Role |
| --- | --- |
| Gregg Bushyeager | Product decisions, AI prompt content, approves flow docs in PRs |
| Hunter Blatz | Co-develops, tests on iOS dev builds |
| Heidi Loiacono | Tests on Android |
| Claude Code | Drafts flow docs, writes code and tests, fixes defects |

## Getting started (Hunter)

1. Accept the GitHub invite to `GMBushyeager/New-GGTeam`.
2. Clone the repo and open it with Claude Code (CLI, desktop, or claude.ai/code).
   The shared settings in `.claude/settings.json` and the slash commands in
   `.claude/commands/` load automatically.
3. Copy `.env.example` to `.env.local` and fill in values you get from Gregg.
   Never commit `.env.local`.
4. Pick up work from an open flow PR, or start a new one with `/flow-draft`.

## Slash commands

| Command | What it does |
| --- | --- |
| `/flow-draft NN-name` | Drafts `docs/flows/NN-name.md` from screenshots and redacted samples |
| `/flow-review NN-name` | Checks a flow doc against the schema, the rules and the template |
| `/parity-check` | Checks that documents the new code writes still parse against the production shape |

## How work flows

1. Draft the flow doc (`/flow-draft`) and open a PR.
2. Gregg approves the flow doc in the PR.
3. Build on `flow/NN-name`: schema → forms → API → UI → tests.
4. Run `/parity-check`.
5. Hunter tests on iOS, Heidi on Android. Defects go back on the same branch.

Build order: 01 sign-in and roles → 02 client list and profile → 03 new
assessment → 04 assessment history → 05 AI brief → 06 reassessment →
07 settings and admin.

## Repo layout

```
apps/mobile/          Expo app
services/api/         Node API
packages/schema/      assessment document types + zod (the contract)
packages/forms/       data-driven form definitions
docs/spec/            Build Spec v0.1 (frozen)
docs/flows/           one approved doc per flow
docs/decisions/       decision records (NNNN-title.md)
docs/reference/       screenshots, redacted sample docs, vendor scopes
.claude/commands/     /flow-draft, /flow-review, /parity-check
```
