# GG Team — Claude Code Project Rules

GYMGUYZ is rebuilding the GG Team trainer assessment app in-house, replacing the
Resourcifi-built app. One Expo codebase ships to iOS and Android. A Node API runs
on AWS. MongoDB is the operational store, and it feeds Snowflake downstream.

Read this file at the start of every session. If a request conflicts with a rule
here, stop and say so rather than working around it.

## People and authority

- **Gregg Bushyeager** owns product decisions and the AI prompt content. Decisions
  happen in pull requests. Do not decide product questions yourself. Write them up
  as open questions in the flow doc.
- **Hunter Blatz** tests on iOS dev builds and co-develops.
- **Heidi Loiacono** tests on Android.
- **Claude Code** drafts flow docs, writes code and tests, and fixes defects.

## Source of truth, in order

1. `packages/schema/`: the assessment document contract (TypeScript + zod)
2. `docs/flows/`: approved flow docs, one per flow
3. `docs/decisions/`: short decision records
4. `docs/spec/`: Build Specification v0.1 (narrative, frozen)
5. `docs/reference/`: current-app screenshots, sample docs, vendor scopes

When these disagree, the higher one wins. Flag the conflict in the pull request.

## Non-negotiable data rules

- **Preserve the `prod.assessments` shape exactly.** Field names stay as they are
  in production, including misspellings such as `assestmentHistory` and
  `metobolic`. Never "correct," rename, re-case or restructure an existing field.
  Snowflake sync and downstream pipelines depend on these names.
- **Every field exists in `packages/schema` before any screen, API route or prompt
  uses it.** No ad hoc fields in components.
- **Add, don't mutate.** New fields are additive and optional at the storage layer,
  even when the UI requires them. Old documents must still parse.
- **Capture raw at the edge, derive downstream.** The app stores what the trainer
  entered or measured. Scores, ages, deltas, triangle profiles and other derived
  values are computed in clearly named, versioned functions. They are never
  overwritten into the raw fields.
- **Own identity.** GG Team keeps its own client and staff IDs. Mindbody IDs are
  stored as external references, never as primary keys.
- **Never write to production.** No prod writes from local code, scripts, tests or
  MCP tools. MongoDB access through MCP uses a read-only user against a dev copy.
- **No real client data in the repo.** Sample documents in `docs/reference/sample-docs/`
  are redacted: no names, phone numbers, emails, addresses or birth dates.
- **No secrets in the repo.** Use environment variables and `.env.local`, which is
  git-ignored.

## Architecture rules

- **Forms are data-driven.** Sections, questions, bubbles, required rules and
  validation live in `packages/forms/` as configuration. Adding or requiring a
  field should be a config change, not a new screen.
- **Role visibility is enforced at the field level.** It is enforced in the API,
  not only hidden in the UI. Trainers never receive financial fields they are not
  allowed to see.
- **AI calls go through the prompt service.** The app never embeds prompt text.
  The API never sends more client data to the model than the prompt needs.
- **Sign-in method is UNRESOLVED.** The options are Entra ID / Microsoft 365 or
  Mindbody credentials. Do not build auth beyond an interface and a stub until a
  decision record exists in `docs/decisions/`.

## Stack

- Mobile: Expo (React Native, TypeScript, strict mode), EAS Build / Submit / Update
- API: Node.js + TypeScript on AWS
- Data: MongoDB Atlas (operational), Snowflake (analytics, downstream only)
- Validation: zod schemas shared from `packages/schema`
- AI: Anthropic API via the GYMGUYZ prompt service

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

## How work flows

1. **Draft the flow doc** in `docs/flows/NN-name.md` using the template below.
   Draft it from the current screenshots and real (redacted) sample documents.
   Mark anything you are unsure of as an open question. Do not guess.
2. **Gregg approves** the flow doc in a pull request.
3. **Build on a branch** named `flow/NN-name`. Update the schema first, then
   forms, then API, then UI, then tests.
4. **Run the parity check.** Documents written by the new code must parse against
   the real production shape.
5. **Device testing.** Hunter tests on iOS and Heidi on Android. Defects go back
   on the same branch.

Build order: 01 sign-in and roles → 02 client list and profile → 03 new
assessment → 04 assessment history (view, edit, comment) → 05 AI brief →
06 reassessment → 07 settings and admin.

## Flow doc template

```
# NN — Flow name
Status: draft | approved | built | verified
Roles: who can use it, and what each role can see
Current screens: deck slide numbers / files in docs/reference/current-screens
What changes: parity | new (source: Resourcifi scope, Simform scope, or GYMGUYZ)
Fields: | label | Mongo path | type | required | validation | visible to |
Behavior: navigation, empty states, errors, offline handling
Derived values: name, inputs, formula, version
Open questions: numbered, each one tagged for Gregg
Acceptance tests: numbered, each one checkable on a device
```

## Writing and style

- Use American English: color, organize, center, analyze.
- Write dates as August 27, 2026 or 8/27/2026.
- Brand tokens: GG Red `#E4002B`, Black `#000000`, GG Grey `#666666`,
  Light Grey `#A8A8A8`, White `#FFFFFF`. Headlines use Oswald (all caps) and body
  text uses Roboto.
- UI copy is plain and short. Trainers use the app in clients' homes.

## Things to stop and ask about

- Any change to an existing production field
- Any new dependency on Mindbody beyond reading data
- Anything touching authentication, payments or health data retention
- Any data or prompt change that affects what the AI brief says about a client
- Any time a flow doc and the current app disagree on behavior
