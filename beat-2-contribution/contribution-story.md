# Contribution: Clarify normsys modifier inputs

Path: `beat-2-contribution/contribution-story.md`

**Contribution Number:** [1]
**Student:** Aayush Kotadia
**GitHub Username:** Aayush7788
**Issue:** https://github.com/scikit-hep/pyhf/issues/1410
**Pull Request:** https://github.com/scikit-hep/pyhf/pull/2786

## Toolkit

### Unit 5: Manual issue scouting and fit checks

I used the course issue-selection site, the issue-scout rubric, and GitHub evidence to screen documentation issues. The GitHub CLI token was invalid, so I could not run the automated scan; I used the rubric directly and recorded this limit instead of claiming an automated result. The site search and rubric surfaced pyhf #1410 as the best fit; an alternate candidate was rejected because its issue says AI-authored PRs will be rejected.

### Unit 6: Claim and upstream policy review

I read pyhf's full CONTRIBUTING.md and the issue thread, then posted a short claim comment from my signed-in GitHub account. The connector could not post comments, so I used GitHub in the browser. The voice-guard hook and local repo memory were not installed because the local clone/auth setup was unavailable; I kept the comment factual and linked it below.

### Unit 7: Plan, documentation change, and PR

The GitHub editor created a focused branch with the documentation clarification and required contributor-list entry, and I opened draft PR #2786. I could not run the local ship-gate or tests because cloning failed through the configured network proxy and the GitHub CLI token was invalid. GitHub checks show pre-commit, CodeFactor, PR-title validation, and the Read the Docs preview build passing. Twelve required checks across six workflows await maintainer approval; CodeRabbit skipped its review because the PR is a draft.

### Unit 8: PR monitoring and playbook

I could not run the local PR monitor because the GitHub CLI token is invalid. I wrote a local playbook draft, checked five recent merged outside-contributor PRs, and used GitHub's read-only PR data to check the current state. As of November 18, the PR remains a draft with no maintainer reviews, so no reply or nudge draft was needed. My playbook uses a five-day wait before one polite nudge; I have not nudged the maintainers.

---

## Why I Chose This Issue

I searched the course issue-selection site with Python and documentation filters and reviewed three possible issues. The pyhf issue is one clear documentation change, has the `good first issue` and `docs` labels, is unassigned, and had no comments or linked PR when I checked it. The repository is active and its CONTRIBUTING.md does not prohibit AI-assisted work. The issue is old (opened in 2021), so I checked the current `docs/likelihood.rst` instead of assuming it was still open work: it still describes `hi` and `lo` as floats without saying plainly that they are relative factors. My manual rubric verdict was **accept, straightforward**; the preferred maintainer-response check was unclear because the issue had no comments.

I rejected Hiero #2730 because its issue says AI bot-authored PRs will be rejected. I also rejected the Thaumonomicon typo candidate because it did not fit my Python documentation focus and sat in a much broader repository. The scout's automated `gh` scan was not available because the local GitHub CLI token was invalid, so I used the rubric and live repository evidence manually. I would add a saved manual evidence report and restore a working CLI token before the next scan. My claim is [here](https://github.com/scikit-hep/pyhf/issues/1410#issuecomment-6719218260).

**Toolkit**

- Tool: Issue-selection site, issue-scout rubric, and GitHub repository/issue evidence, applied manually.
- What it produced: A screened set of three candidates and an accept verdict for pyhf #1410.
- Difficulties: The automated scan could not run with the invalid GitHub CLI token; the old issue also had no response history to grade.
- What changed: I checked the current docs and implementation directly, chose a small documentation-only scope, and recorded the automated-scan limitation honestly.

---

## Understanding the Issue

**Problem Description**

The `normsys` documentation gives `hi` and `lo` values as floats but does not clearly tell readers that they are multiplicative factors, not absolute event counts.

**Expected Behavior**

The docs should say that `hi` and `lo` scale nominal sample rates and show how example values change those rates.

**Current Behavior**

The docs explain the interpolation endpoints and show `hi: 1.1` and `lo: 0.9`, but do not state explicitly that these are relative scale factors.

**Affected Components**

`docs/likelihood.rst`, the generated normsys API documentation, and the implementation in `src/pyhf/modifiers/normsys.py`. This patch changes the likelihood documentation and the contributor list only; the generated API page has no separate source docstring describing these inputs.

**Toolkit**

- Tool: GitHub source viewer and issue-scout/repro-check criteria.
- What it produced: A trace from issue #1410 to the `normsys` section and `normsys_builder.collect`.
- Difficulties: The local clone was unavailable, so the repository could not be inspected with local search tools.
- What changed: I kept the change within the documented issue and verified the example against the visible implementation source.

---

## Reproduction Process

**Environment Setup**

Windows 11, Git 2.55.0, and the signed-in GitHub browser. The target source was pyhf `main` at base commit `2c99d0b7cfa703c3798c6588312857c5b3e97d51`. `gh auth status` reported an invalid keyring token, and `git clone` could not connect through the configured proxy. I therefore compared the issue with the live GitHub source and editor; I could not create a local checkout or run a local documentation build.

**Steps to Reproduce**

1. Open issue #1410 and read its question about absolute counts versus relative scale factors.
2. Open `docs/likelihood.rst` on `main` and find “Normalisation Uncertainty (normsys)”.
3. Compare the prose with its `hi: 1.1`, `lo: 0.9` example: the factors are named as floats, but the text does not explicitly distinguish them from event counts.

**Reproduction Evidence**

- **Commit showing reproduction:** none; I could not make a local reproduction commit.
- **Screenshots/logs:** GitHub source and issue were inspected in the signed-in browser. The clone failure was: `Failed to connect to github.com:443 over proxy 127.0.0.1`.
- **My findings:** The issue is a documentation ambiguity, not a runtime failure. In `normsys_builder.collect`, `lo` and `hi` are used as the modifier endpoint factors; the docs needed to say what those numbers mean to a reader.

**Toolkit**

- Tool: GitHub issue/source viewer and the repro-check evidence checklist.
- What it produced: A repeatable source-based check showing the missing explanation.
- Difficulties: No local checkout, executable reproduction, or screenshot file was available.
- What changed: I used the issue text and current source as the reproduction evidence and did not claim a local test or commit.

---

## Solution Approach

**Analysis**

The issue is caused by missing explanatory text. `normsys_builder.collect` reads the `lo` and `hi` values and supplies them as the downward and upward modifier endpoints; the surrounding likelihood docs identify the interpolation but do not say plainly that the values are relative multipliers rather than yields.

**Proposed Solution**

Explain that the values multiply nominal sample rates, show that 1.1 and 0.9 mean a 10% increase and decrease at the endpoints, and link to the HistFactory modifier table. I did not change model behavior, APIs, or tests.

**Implementation Plan**

1. Clarify the relative-factor meaning in `docs/likelihood.rst`.
2. Give a two-bin numerical example and link to `tab:modifiers_and_constraints`.
3. Add my name to `docs/contributors.rst`, as required by CONTRIBUTING.md, then check the diff and open a draft PR.

**Toolkit**

- Tool: GitHub source viewer, issue statement, and a written plan checked against the repository instructions.
- What it produced: A two-file documentation-only change tied to issue #1410.
- Difficulties: The plan-check command could not run without the local skill environment and clone.
- What changed: I kept the patch limited to the requested clarification and required contributor entry.

---

## Testing Strategy

The repository recommends a warning-free Sphinx build with `pixi run -e docs build-docs` and pytest with `pytest --ignore=tests/test_notebooks.py`. I could not run either locally because the clone failed. On PR #2786, GitHub reports success for the Read the Docs preview build, pre-commit, CodeFactor, and PR-title validation. Twelve required checks across six workflows await maintainer approval; CodeRabbit skipped its review because the PR is a draft. The pytest suite was not run locally, and no maintainer review has arrived yet.

**Toolkit**

- Tool: Repository check instructions and GitHub PR check diagnostics.
- What it produced: The exact local check commands and live CI results for the draft PR.
- Difficulties: Local Sphinx and pytest checks were not available without a clone; Read the Docs build succeeded.
- What changed: I marked the local checks unrun and reported each remote check by its actual state.

---

## Implementation Notes

**November 8, 2026**

Read the issue and current source, checked CONTRIBUTING.md, posted a claim comment, and created a fork. Committed the scale-factor explanation on `docs/clarify-normsys-scale-factors`, then added my contributor name. Opened draft PR #2786 against `scikit-hep/pyhf:main`. The diff has no reported conflicts; pre-commit, CodeFactor, title validation, and the Read the Docs preview passed; twelve required checks across six workflows await maintainer approval, and CodeRabbit skipped review for draft status. Local tests remain unrun because the clone and CLI authentication failed.

**November 18, 2026**

Rechecked PR #2786 through GitHub's read-only PR data before finalizing this story. The PR is still open and marked draft, with no maintainer reviews or new maintainer feedback. I updated the status and Unit 8 entry to record that current state and did not post a nudge.

**Toolkit**

- Tool: Signed-in GitHub browser and GitHub PR diagnostics.
- What it produced: Two commits, a reviewed two-file diff, and draft PR #2786.
- Difficulties: The browser editor did not provide local test execution, and the CLI credentials were invalid.
- What changed: I verified the remote diff and CI state and left the PR as a draft for review.

---

## Pull Request

**PR Link:** https://github.com/scikit-hep/pyhf/pull/2786

**PR Description:** Clarifies that `normsys` `hi` and `lo` are relative multiplicative scale factors, not absolute event counts. Adds the endpoint example `[10, 20]` → `[11, 22]` and `[9, 18]`, links to the HistFactory modifier table, adds my contributor name, and references issue #1410 with `Fixes #1410`. The description discloses that local tests were not run when opened. It also states that AI helped draft the wording and that I checked the example against the source.

**Maintainer Feedback:**

- November 18, 2026: None yet. The PR has no maintainer reviews; the only thread activity is the earlier CodeRabbit notice that draft PRs are not automatically reviewed.

**Status:** Draft and awaiting maintainer review. The PR is open and mergeable; its last recorded CI result has four passing checks, while twelve required checks across six workflows await maintainer approval.

**Toolkit**

- Tool: GitHub PR data, check diagnostics, and a manual review-time check of five merged contributor PRs.
- What it produced: Draft PR #2786, a current status snapshot, and a local playbook draft. The local monitor itself did not run.
- Difficulties: The GitHub CLI token was invalid, so the local PR-monitor command could not run.
- What changed: I used GitHub's read-only status to update the story and left the PR as a draft under pyhf rules.

---

## Learnings and Reflections

**Technical Skills Gained**

I learned how `normsys` endpoint factors relate to the nominal sample rates, how to trace a documentation issue to the implementation, and how to use a two-bin example to explain relative scaling.

**Challenges Overcome**

The local clone and GitHub CLI were unavailable. I used the signed-in browser to create a fork, branch, commits, and draft PR, then used the GitHub connection to read the diff and CI results. I did not claim tests I could not run.

**What I'd Do Differently Next Time**

I would verify GitHub CLI authentication and clone the repository before claiming an issue, so I could run the documentation build locally and use the issue-scout, voice-guard, ship-gate, and PR-monitor commands as intended.

---

## Resources Used

- [Issue #1410 and claim comment](https://github.com/scikit-hep/pyhf/issues/1410#issuecomment-6719218260)
- [pyhf contribution guide](https://github.com/scikit-hep/pyhf/blob/main/CONTRIBUTING.md)
- [Likelihood documentation](https://github.com/scikit-hep/pyhf/blob/main/docs/likelihood.rst)
- [HistFactory modifier table](https://github.com/scikit-hep/pyhf/blob/main/docs/intro.rst#tab:modifiers_and_constraints)
- [Draft PR #2786 and CI checks](https://github.com/scikit-hep/pyhf/pull/2786)
