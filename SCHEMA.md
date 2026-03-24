# DID JSON Schema v2.0

All files in `dids/` conform to this schema.

## Top-Level Fields

| Field | Type | Description |
|---|---|---|
| `document_number` | string | Official DID number, e.g. `"DI-SESS-81248B"` |
| `slug` | string | URL-safe identifier, e.g. `"di-sess-81248b"` |
| `title` | string | Full document title |
| `summary` | string | Brief description of purpose |
| `approval_date` | string | ISO date, e.g. `"2015-04-07"` |
| `amsc_number` | string | Acquisition Method Suffix Code |
| `limitation` | string | Distribution limitation |
| `dtic_applicable` | string | `"Yes"` or `"No"` |
| `gidep_applicable` | string | `"Yes"` or `"No"` |
| `office_of_primary_responsibility` | string | OPR code |
| `preparing_activity` | string | Preparing activity code, e.g. `"MI"`, `"NM"`, `"AR"` |
| `project_number` | string | Project number |
| `applicable_forms` | string | Form references |
| `form_version` | string | Form version (may be empty) |
| `use_relationship` | string | Multi-paragraph prose description; paragraphs separated by `\n` |
| `supersedes` | string[] | Document numbers this DID replaces |
| `related_dids` | string[] | Related DID document numbers |
| `references` | Reference[] | External references (see below) |
| `distribution_statement` | string | Full distribution statement text |
| `requirements` | Requirement[] | Recursive requirements tree (see below) |
| `_source` | Source | Extraction metadata |
| `_schema_version` | string | Always `"2.0"` |

## Reference Object

```json
{
  "label": "Descriptive text for the reference",
  "url": "https://example.com"
}
```

## Requirement Object (recursive)

```json
{
  "number": "3.1.a",
  "title": "Short title of the requirement",
  "content": "The body text of the requirement.",
  "asterisk": false,
  "children": []
}
```

| Field | Type | Description |
|---|---|---|
| `number` | string | Requirement number, e.g. `"3"`, `"3.a"`, `"3.1.b"` |
| `title` | string | Short title |
| `content` | string | Body text (may be empty if children carry all content) |
| `asterisk` | boolean | `true` if the requirement is tailorable |
| `children` | Requirement[] | Nested sub-requirements (same structure) |

## Source Object

```json
{
  "source_file": "DI-SESS-81248B.pdf",
  "extraction_date": "2026-03-24",
  "extraction_method": "manual"
}
```

## Example

See any file in `dids/` for a complete example.
