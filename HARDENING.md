<!-- markdownlint-disable -->

# Hardening Report: Madrapps--jacoco-report/v1.7.2

> This file was generated automatically by the hardening agent.

**Policy SHA:** `374911c4be584df24e6da57af2d990570ef0f859`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **Madrapps--jacoco-report/v1.7.2** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### prior-fix (severity: high)

Carried forward from this version's previous harden, which fixed it; fix it again unless the code no longer has the problem. The previous harden changed action.yml without recording a finding for it, and this analysis reported nothing there. Re-apply its security changes unless the code no longer needs them. The previous patch:
```diff
diff --git a/action.yml b/action.yml
index bb9099f..2669a68 100644
--- a/action.yml
+++ b/action.yml
@@ -53,17 +53,15 @@ inputs:
     description: 'Run the action in debug mode and get debug logs printed in console'
     required: false
     default: 'false'
-
 outputs:
   coverage-overall:
     description: 'The overall coverage of the project'
   coverage-changed-files:
     description: 'The total coverage of all changed files'
-
 runs:
   using: 'node20'
   main: 'dist/index.js'
-
 branding:
   icon: 'percent'
   color: 'green'

```

Locations:

- `action.yml`

## Iteration Notes

### Iteration 1

**Notes:**

No changes made. The 'prior-fix' patch only removed blank lines from action.yml, so it changed formatting and fixed nothing. action.yml runs dist/index.js on node20 and has no uses:, run: steps, ${{ }} expressions or hardcoded credentials, so it has no security problem to fix. Re-applying a whitespace-only change would not improve security.

