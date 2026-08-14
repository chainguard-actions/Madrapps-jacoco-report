<!-- markdownlint-disable -->

# Hardening Report: Madrapps--jacoco-report/v1.7.2-beta

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **Madrapps--jacoco-report/v1.7.2-beta** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### missing-permissions (severity: medium)

The workflow file .github/workflows/check.yml has no top-level `permissions:` key and the single job `build` also has no job-level `permissions:` key. Without explicit permissions, the GITHUB_TOKEN is granted its default (potentially broad) permissions, which may include write access to repository contents and pull requests.

Locations:

- `.github/workflows/check.yml:1`

### unpinned-uses (severity: high)

The workflow file .github/workflows/check.yml references two actions using mutable tag refs instead of pinned full SHA commits:
- `uses: actions/checkout@v4` (line 16) — should be pinned to a full 40-character commit SHA
- `uses: actions/setup-node@v4` (line 19) — should be pinned to a full 40-character commit SHA

Mutable tags can be moved by the upstream repository owner, enabling supply-chain attacks where a compromised or malicious tag update executes arbitrary code in your workflow.

Locations:

- `.github/workflows/check.yml:16`
- `.github/workflows/check.yml:19`

## Iteration Notes

### Iteration 1

**Fixes applied:** missing-permissions, unpinned-uses

**Notes:**

Fixed .github/workflows/check.yml: (1) Added top-level `permissions: contents: read` to restrict GITHUB_TOKEN to minimum required access. (2) Pinned actions/checkout@v4 to full SHA 34e114876b0b11c390a56381ad16ebd13914f8d5 and actions/setup-node@v4 to full SHA 49933ea5288caeca8642d1e84afbd3f7d6820020, with original tags preserved as inline comments.

