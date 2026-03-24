# Contributing to DID Data

Thanks for helping improve this resource. Here's how to contribute.

## Adding a New DID

1. **Get the source** — Download the original DID PDF from [ASSIST](https://assist.dla.mil)
2. **Create the JSON** — Follow the schema in `SCHEMA.md`. Name the file after the slug, e.g. `di-sess-81248b.json`
3. **Place it** — Put the file in the `dids/` directory
4. **Open a PR** — Include the document number, title, and a link to the ASSIST entry in your PR description

## Correcting an Existing DID

1. Edit the relevant JSON file in `dids/`
2. Open a PR explaining what was wrong and what the correct text is
3. Include a reference to the authoritative source (ASSIST URL, page number, etc.)

## JSON Schema

See `SCHEMA.md` for the full field reference. Key rules:

- `slug` must be URL-safe and unique (lowercase, hyphens only, e.g. `di-sess-81248b`)
- `requirements` is a recursive tree — children can have children
- `asterisk: true` marks a tailorable requirement
- All arrays (`supersedes`, `related_dids`, `references`, `children`) should be empty arrays `[]`, never `null`
- `_schema_version` must be `"2.0"`

## What Not to Submit

- Content copied from non-authoritative sources
- Interpretations or commentary — only verbatim DID text
- DIDs already in the repo (check first)
