# @ggteam/schema

The assessment document contract: TypeScript types plus zod schemas. This is the
top source of truth.

- Mirror `prod.assessments` exactly, including misspellings (`assestmentHistory`,
  `metobolic`).
- New fields are additive and optional.
- Every field lands here before any screen, API route or prompt uses it.
