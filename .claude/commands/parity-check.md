---
description: Check that documents written by the new code parse against the real production shape
---

Run the parity check for the current branch.

1. Find the zod schemas in `packages/schema/` and the redacted production samples
   in `docs/reference/sample-docs/`.
2. Confirm every sample still parses against the current schema (old documents
   must keep working).
3. Confirm that documents produced by the new code (fixtures and test output)
   use only field names that exist in production or are newly added and
   optional. Flag any renamed, re-cased or restructured field, including fixed
   misspellings like `assestmentHistory` or `metobolic`.
4. Confirm that no derived value is written into a raw field.
5. If a MongoDB MCP connection is used, it must be read-only against the dev
   copy. Never write anything.

Report pass or fail per check, with file and field paths for each failure.
