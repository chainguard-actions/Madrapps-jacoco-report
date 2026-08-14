<!-- markdownlint-disable -->

# Hardening Report: Madrapps--jacoco-report/v1.8.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **Madrapps--jacoco-report/v1.8.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow file uses action references pinned to mutable version tags instead of immutable 40-character commit SHAs. This exposes the workflow to supply-chain attacks if the upstream action tag is moved or compromised. Failing references: `actions/checkout@v4` and `actions/setup-node@v4`. These should be pinned to their full SHA digests, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`.

Locations:

- `.github/workflows/check.yml:16`
- `.github/workflows/check.yml:20`

### missing-permissions (severity: medium)

The workflow file has no top-level `permissions:` key and the `build` job also has no job-level `permissions:` key. Without explicit permissions, the workflow inherits the repository's default token permissions (which may be `write-all` for older repositories), granting broader access than necessary. A minimal permissions block (e.g. `permissions: contents: read`) should be added at the top level or on each job.

Locations:

- `.github/workflows/check.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

In hardened/action/.github/workflows/check.yml: (1) Added top-level `permissions: contents: read` block to satisfy least-privilege requirement. (2) Pinned `actions/checkout@v4` to `actions/checkout@11d5960a326750d5838078e36cf38b85af677262 # v4` and `actions/setup-node@v4` to `actions/setup-node@49933ea5288caeca8642d1e84afbd3f7d6820020 # v4` using resolved commit SHAs.

