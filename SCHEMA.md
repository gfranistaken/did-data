# DID JSON Schema v3.0

All files in `dids/` conform to this schema.

## Top-Level Fields

| Field | Type | Description |
|---|---|---|
| `document_number` | string | Official DID number, e.g. `"DI-SESS-81248B"` |
| `slug` | string | URL-safe identifier, e.g. `"di-sess-81248b"` |
| `title` | string | Full document title |
| `summary` | string | Brief description of purpose |
| `approval_date` | string | ISO date, e.g. `"2015-04-07"` |
| `did_format` | string | `"dd_form_1664"` for pre-2014 DIDs; `"free_text"` for MIL-STD-963C (2014+) DIDs |
| `963c_compliant` | boolean | `true` if prepared under MIL-STD-963C (2014 or later) |
| `amsc_number` | string | Acquisition Method Suffix Code |
| `limitation` | string | Distribution limitation |
| `dtic_applicable` | string | `"Yes"` or `"No"` |
| `gidep_applicable` | string | `"Yes"` or `"No"` |
| `office_of_primary_responsibility` | string | OPR code |
| `preparing_activity` | string | Preparing activity code, e.g. `"MI"`, `"NM"`, `"AR"` |
| `project_number` | string | Project number |
| `applicable_forms` | string | Form references |
| `approval_limitation` | string | Approval limitation (may be empty) |
| `form_version` | string | Form version (may be empty) |
| `use_relationship` | string | Multi-paragraph prose description; paragraphs separated by `\n` |
| `description_purpose` | string | DD Form 1664 "Description/Purpose" field (empty for free-text DIDs) |
| `application_interrelationship` | string | DD Form 1664 "Application/Interrelationship" field (empty for free-text DIDs) |
| `supersedes` | string[] | Document numbers this DID replaces |
| `related_dids` | string[] | Related DID document numbers |
| `references` | Reference[] | External references (see below) |
| `distribution_statement` | string | Full distribution statement text |
| `preparation_instructions` | Requirement[] | Recursive requirements tree (see below); formerly `requirements` |
| `_source` | Source | Extraction metadata |
| `_schema_version` | string | Always `"3.0"` |
| `_schema_notes` | object | Human-readable field-level documentation embedded in each file |

## Reserved Fields

Fields marked as reserved are always present in every file but will be empty string `""` or empty array `[]` when not applicable to the DID's format:
- `description_purpose` and `application_interrelationship` — populated for `dd_form_1664`, empty for `free_text`
- `use_relationship` — populated for `free_text`, typically empty for `dd_form_1664`

## Reference Object

```json
{
  "label": "Descriptive text for the reference",
  "url": "https://example.com"
}
```

## Requirement Object (recursive)

Section numbers are normalized to strictly numeric dot-notation. Letter-based source numbering (e.g. `2.a`, `3.1.b`) is converted to numeric equivalents (`2.1`, `3.1.2`).

```json
{
  "number": "3.1",
  "title": "Short title of the requirement",
  "content": "The body text of the requirement.",
  "asterisk": false,
  "children": []
}
```

| Field | Type | Description |
|---|---|---|
| `number` | string | Requirement number in numeric dot-notation, e.g. `"3"`, `"3.1"`, `"3.1.2"` |
| `title` | string | Short title |
| `content` | string | Body text (may be empty if children carry all content) |
| `asterisk` | boolean | `true` if the requirement is conditionally applicable (marked `*` in source) |
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
