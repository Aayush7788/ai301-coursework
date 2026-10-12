---
name: pr-precheck
description: Grade one pull request package against its issue, accepted plan, diff, tests, and repository rules; decide whether it is ready to submit. Use before opening a PR or to grade a frozen eval package.
---

# pr-precheck: rubric-driven PR grading

Grade one PR package to answer only: **is this ready to submit?** Read the candidate change against the issue and the plan it claims to implement. Do not grade from polish or intuition; execute the checks in `rubric.md` using `procedure.md` and `references/evidence-guide.md`.

## Inputs and modes

Choose one mode from the request.

- **Live mode:** grade the student's own PR draft for an issue URL. Read `plan.md` (including `## Deviations`), the branch's committed change from `git diff main...HEAD` in the working copy, the draft PR title and description in `pr_draft.md`, and `test_evidence.md`. Read the issue and its thread, the scoped repository's `.github/PULL_REQUEST_TEMPLATE.md`, and `docs/CONTRIBUTING.md` and other directly relevant written repository policies. A house-chain student uses the assigned house plan and repro pack instead of a personal posted plan or repro. Grade only what is present in these inputs; do not assume a draft is already open or that CI has run.
- **Eval mode:** use only the supplied package bundle. It contains the issue, thread highlights, repo facts, accepted plan and repro context, candidate title, description, commits, diff, and test evidence. Fetch nothing, read no other files, and grade the complete package using every rubric check and the full verdict rule.

## The scope seam (live mode only)

Read `scope.md` before any other live evidence. Grade only PRs targeting the exact repository on its `Repo:` line. If that line is a placeholder or the target repository/issue is outside scope, refuse to grade and explain why. Never guess the repository. Eval mode ignores `scope.md` entirely.

## The voice seam (live mode only)

Read `voice-guide.md` and compare its concrete rules with the PR title and description. Briefly report any broken rule in the readable summary. The voice guide does not change the verdict unless a rubric check explicitly makes the same issue a verdict criterion. Eval mode ignores the voice guide entirely.

## Component reads

`rubric.md` defines the checks, their required or preferred weights, and how grades produce the verdict. `references/evidence-guide.md` maps each evidence family to the package or live source. Execute `procedure.md` in its stated order. If it is silent on a step, report the gap instead of inventing a rule. If the rubric has no checks or the procedure has no steps, refuse to grade and say which component is empty.

## Verdict and output

Use only the binary verdicts: `accept` means ready to submit; `reject` means hold. Give every rubric check its exact name, a grade, and one concise evidence line citing a quote or observable fact. End with this valid fenced JSON block, with nothing after it; keep its schema and order unchanged:

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

- Require a specific fact or quote for every grade; "looks good" is not evidence.
- Grade the change itself against the issue, the accepted plan and deviations, observable tests, and written repository requirements. Concision or polish alone is never a defect.
- The rubric determines whether a condition passes; do not override it based on preference. The procedure determines what to read and compare; report missing steps rather than improvising.
- Treat `unclear` as a failure for required checks; an unverifiable claim is not ready. Preferred checks never change the verdict.
