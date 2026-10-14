---
description: Draft a flow doc in docs/flows/ from current screenshots and redacted sample documents
argument-hint: NN-name (for example 03-new-assessment)
---

Draft the flow doc `docs/flows/$ARGUMENTS.md`.

1. Re-read `CLAUDE.md`, then read `docs/flows/_TEMPLATE.md`.
2. Gather sources in priority order: `packages/schema/`, approved docs in
   `docs/flows/`, `docs/decisions/`, `docs/spec/`, then `docs/reference/`
   (current-screens, sample-docs, vendor-scopes).
3. Fill every template section. For each field, give the exact Mongo path as it
   appears in production, including misspellings. Never "correct" a name.
4. Mark each field as parity or new, and cite the source (Resourcifi scope,
   Simform scope, or GYMGUYZ).
5. Anything you can't confirm from a source goes under Open questions, tagged
   `(Gregg)`. Do not guess.
6. Write acceptance tests that someone can check on a device.
7. Set `Status: draft`. Do not create the build branch. Gregg approves the flow
   doc in a PR first.

At the end, list the sources you used and every conflict you found between them.
