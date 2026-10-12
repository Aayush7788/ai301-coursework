# Evidence Guide: where PR evidence lives

## Plan fidelity

### Where it lives
In an eval bundle, compare the Issue and Thread highlights, accepted plan context, candidate PR description, commits, and unified diff. In live mode, compare the posted or supplied plan (including `## Deviations`), issue thread, title/description in `pr_draft.md`, and the committed output of `git diff main...HEAD`.

### What good looks like
Every material diff hunk is requested by the plan or explained as a deviation in the updated plan and description; every material planned change is delivered or honestly recorded as deferred. The description's claims about the diff are accurate. A smaller useful slice can be ready when its boundary and deferral are clear and tested.

## Test evidence

### Where it lives
In eval, use the candidate's Test evidence plus the plan's test plan, issue repro, and repo-facts asks. In live mode, use `test_evidence.md`, the plan, the posted repro or house repro pack, and the repository's documented checks.

### What good looks like
The output demonstrates the reported behavior on the changed path and the expected after result, with before/after evidence for a reproduced bug. A relevant regression test or focused test result supports the fix. For closely related variants implemented with the same fix shape, the primary repro plus a regression test can be enough when the diff visibly applies the fix to every variant; demand separate evidence for distinct behaviors or code paths. A control that never failed is not proof by itself. Named tests and required local checks have observable results, and failures or unavailable checks are disclosed accurately.

## Diff quality

### Where it lives
The complete unified diff and commit summary in an eval bundle; the committed `git diff main...HEAD` and commit summary in live mode.

### What good looks like
The diff is focused and lets a reviewer trace the planned fix. Debug prints, dead probes, commented-out attempts, unrelated changes, or mechanical churn are defects when they materially obscure or burden review. Do not penalize routine formatting needed to make the actual change consistent.

## Standards and communication

### Where it lives
In eval, use the Repo facts block, Thread highlights, PR title, description, diff, and test evidence. In live mode, use `.github/PULL_REQUEST_TEMPLATE.md`, `docs/CONTRIBUTING.md`, relevant written repository policies, the issue thread, `pr_draft.md`, the diff, and `test_evidence.md`.

### What good looks like
Every applicable required template section and explicit checklist ask is addressed with accurate content; required issue references and repository artifacts are present. Follow direct maintainer constraints and disclose AI use when the repository explicitly requires it. Do not claim post-open CI is green before it has run or require disclosure when no policy asks for it.

## Description accuracy

### Where it lives
Compare each factual claim in the candidate PR title and description with the diff, accepted plan/deviations, and actual test output. Eval uses only the bundle. Live mode uses `pr_draft.md`, `plan.md`, `git diff main...HEAD`, and `test_evidence.md`.

### What good looks like
Claims about behavior, scope, test results, and readiness match observable evidence. A limitation or partial delivery is stated plainly and consistently with the plan's deviation record; a claim that the diff includes a missing file or test fails.
