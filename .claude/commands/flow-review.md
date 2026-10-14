---
description: Review a flow doc against the schema, the project rules and the template
argument-hint: NN-name
---

Review `docs/flows/$ARGUMENTS.md`. Do not edit it; report findings.

Check:
1. Every template section is present and filled.
2. Every field's Mongo path exists in `packages/schema/`, or the doc says the
   schema change is additive and optional.
3. No existing production field is renamed, re-cased or restructured.
4. Derived values have a name, inputs, formula and version, and are not stored
   in raw fields.
5. `visible to` is set for every field, and financial fields are restricted.
6. Nothing builds auth beyond an interface and stub unless a decision record exists.
7. Anything in the "Things to stop and ask about" list in `CLAUDE.md` is raised
   as an open question for Gregg.
8. Acceptance tests can be checked on a device.
9. Dates and spelling follow American English.

Report as a numbered list: blocking findings first, then nits.
