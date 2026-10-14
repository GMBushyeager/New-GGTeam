## What this changes

Flow: `NN-name` (link the flow doc)

## Checklist

- [ ] Every new field exists in `packages/schema` first
- [ ] No existing `prod.assessments` field renamed, re-cased or restructured
- [ ] New fields are additive and optional at the storage layer; old documents still parse
- [ ] Derived values live in named, versioned functions, not in raw fields
- [ ] Role visibility enforced in the API, not only the UI
- [ ] No secrets, no real client data, no prod writes
- [ ] `/parity-check` passes
- [ ] Tested on iOS (Hunter) / Android (Heidi)

## Conflicts between sources of truth

None, or describe which source wins and why.

## Open questions for Gregg

1.
