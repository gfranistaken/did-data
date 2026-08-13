# DID Data Repository

Community-maintained, machine-readable repository of DoD Data Item Descriptions (DIDs) in JSON format.

## What's Here

- `dids/<type>/` — One JSON file per DID, conforming to schema v2.0, sharded by DID type prefix (e.g. `dids/sess/` for `DI-SESS-*`)
- `SCHEMA.md` — Full schema reference
- `CONTRIBUTING.md` — How to add or correct a DID

## How It Works

This repo is the **data source** for [DIDfinder](https://didfinder.com) ([source](https://github.com/gfranistaked/did-registry)). When a change is merged to `master`, a GitHub Action automatically triggers a rebuild of the site.

## Adding a DID

1. Add a new `.json` file to `dids/<type>/` (the lowercase type prefix from the DID number, e.g. `dids/sess/` for `DI-SESS-81248B`) following the schema in `SCHEMA.md`
2. Open a pull request with a brief description of the DID and its source

All submissions are validated against the schema before merge.

## Verifying DIDs

The authoritative source for all DIDs is the [ASSIST database](https://assist.dla.mil). Always verify content against the official record before submitting.
