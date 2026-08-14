<!-- markdownlint-disable -->

# Hardening Report: Madrapps--jacoco-report/v1.7.2-alpha

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **Madrapps--jacoco-report/v1.7.2-alpha** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow file .github/workflows/check.yml references two actions using mutable version tags instead of full 40-character commit SHAs. This exposes the workflow to supply-chain attacks if the tag is moved or the upstream repository is compromised. Failing references: `actions/checkout@v4` (line 16) and `actions/setup-node@v4` (line 19). These should be pinned to their full SHA digests, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`.

Locations:

- `.github/workflows/check.yml:16`
- `.github/workflows/check.yml:19`

### missing-permissions (severity: medium)

The workflow file .github/workflows/check.yml has no top-level `permissions:` block and the only job (`build`) also has no job-level `permissions:` block. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad (e.g. write access to contents). A minimal explicit permissions block such as `permissions: read-all` or specific scopes (e.g. `contents: read`) should be added.

Locations:

- `.github/workflows/check.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

In .github/workflows/check.yml: (1) Added top-level `permissions: contents: read` block to satisfy the missing-permissions finding. (2) Pinned `actions/checkout@v4` to `actions/checkout@11d5960a326750d5838078e36cf38b85af677262 # v4` and `actions/setup-node@v4` to `actions/setup-node@49933ea5288caeca8642d1e84afbd3f7d6820020 # v4` to satisfy the unpinned-uses finding.

