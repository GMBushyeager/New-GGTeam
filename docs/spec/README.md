# Build Specification v0.1

[`build-spec-v0.1.md`](build-spec-v0.1.md) is the narrative build spec, dated
September 26, 2026. It is **frozen**: do not edit it. Changes and resolutions go
in decision records (`docs/decisions/`) or flow docs (`docs/flows/`), which rank
above the spec.

## Known conflicts with higher sources

- **Sign-in.** The spec describes Microsoft Entra ID sign-in (§3, §4, §5,
  acceptance tests 1–2), but §12 still asks whether every trainer has a
  Microsoft 365 account, and `CLAUDE.md` marks sign-in as unresolved. Until a
  decision record exists in `docs/decisions/`, build auth only as an interface
  and a stub.
