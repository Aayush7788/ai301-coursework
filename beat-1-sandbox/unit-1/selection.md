# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73

**Verdict output**

Summary of checks across all three issues:

**All three issues share the same positive signals:**

- **AI policy**: No CONTRIBUTING.md-level AI ban; CONTRIBUTING.md at **`docs/CONTRIBUTING.md`** and PR template have no AI restrictions. Silence passes.
- **Maintainer alive**: 5 human commits by Andrew Burke, most recent Sep 16, 2026. Well within 90 days.
- **Already being worked on**: All three have empty assignee lists, zero linked PRs, and zero comments (no claims).
- **Repository active/in use**: Not archived, last push Sep 16, 2026. No formal releases but commit activity is recent.

**Scope differentiation:**

- **#73** (env discrepancy): 1–2 hrs, docs-only fix — simplest.
- **#72** (password hash bug): 1–2 hrs, code + test fix with xfail removal — straightforward single function.
- **#69** (output parser crash): 2–4 hrs, code + test fix with xfail removal — slightly broader.

**Maintainer response**: No comments on any of the three, so **`unclear`** across the board (preferred check, does not affect verdict).

**Ranked (all accepted, fit-ordered by effort and scope simplicity):**

1. **#73** — Documentation-only fix, lowest effort, most accessible for a newcomer.
2. **#72** — Single-function bug fix, well-bounded, 1–2 hours.
3. **#69** — Bug fix with fallback path, slightly wider scope, 2–4 hours.

```json
[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73",
    "checks": [
      {"name": "AI policy", "grade": "pass", "evidence": "No CONTRIBUTING.md-level AI ban; docs/CONTRIBUTING.md and PR template contain no AI restrictions. Silence passes per rubric."},
      {"name": "Maintainer alive", "grade": "pass", "evidence": "Last 5 commits by Andrew Burke (human), most recent 2026-09-16, within 90 days."},
      {"name": "Scope", "grade": "pass", "evidence": "Single bounded objective: make README and .env.example agree on OPENROUTER_API_KEY and LLM_PROVIDER values. Files named, effort estimated 1-2 hours."},
      {"name": "Already being worked on", "grade": "pass", "evidence": "No assignees, zero linked PRs, zero comments on the issue."},
      {"name": "Repository active/in use", "grade": "pass", "evidence": "Not archived, last push 2026-09-16, 2 stars, recent commit activity within 90 days."},
      {"name": "Maintainer response", "grade": "unclear", "evidence": "No comments on this issue; insufficient sample to assess responsiveness. Preferred check — does not gate verdict."}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/72",
    "checks": [
      {"name": "AI policy", "grade": "pass", "evidence": "No CONTRIBUTING.md-level AI ban; docs/CONTRIBUTING.md and PR template contain no AI restrictions. Silence passes per rubric."},
      {"name": "Maintainer alive", "grade": "pass", "evidence": "Last 5 commits by Andrew Burke (human), most recent 2026-09-16, within 90 days."},
      {"name": "Scope", "grade": "pass", "evidence": "Single bounded objective: catch UnknownHashError in verify_password and return False instead of raising. Two files named, effort estimated 1-2 hours, xfail marker to remove."},
      {"name": "Already being worked on", "grade": "pass", "evidence": "No assignees, zero linked PRs, zero comments on the issue."},
      {"name": "Repository active/in use", "grade": "pass", "evidence": "Not archived, last push 2026-09-16, 2 stars, recent commit activity within 90 days."},
      {"name": "Maintainer response", "grade": "unclear", "evidence": "No comments on this issue; insufficient sample to assess responsiveness. Preferred check — does not gate verdict."}
    ],
    "verdict": "accept"
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s3/issues/69",
    "checks": [
      {"name": "AI policy", "grade": "pass", "evidence": "No CONTRIBUTING.md-level AI ban; docs/CONTRIBUTING.md and PR template contain no AI restrictions. Silence passes per rubric."},
      {"name": "Maintainer alive", "grade": "pass", "evidence": "Last 5 commits by Andrew Burke (human), most recent 2026-09-16, within 90 days."},
      {"name": "Scope", "grade": "pass", "evidence": "Single bounded objective: handle top-level JSON array in output_parser.py fallback path instead of crashing with AttributeError. Two files named, effort estimated 2-4 hours, xfail marker to remove."},
      {"name": "Already being worked on", "grade": "pass", "evidence": "No assignees, zero linked PRs, zero comments on the issue."},
      {"name": "Repository active/in use", "grade": "pass", "evidence": "Not archived, last push 2026-09-16, 2 stars, recent commit activity within 90 days."},
      {"name": "Maintainer response", "grade": "unclear", "evidence": "No comments on this issue; insufficient sample to assess responsiveness. Preferred check — does not gate verdict."}
    ],
    "verdict": "accept"
  }
]
```

**The verdict must record `accept` for this issue.** The live output above records `"verdict": "accept"` for issue #73.

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

> `agreement: 17/20 scored items (bar: 18/20: below the bar)`

This is the final complete full eval run, and this is the score that must match the agreement line in the submitted `eval-run.txt`.

**Issue analysis**

> `issue-15` — rubric decision: **reject**; gold label: **reject**.

The rubric reached `reject` because the required Scope check is designed to fail an issue when its history contains repeated implementation attempts that ended without a settled resolution. Issue #15 had repeated implementation attempts and closed/unmerged PRs without a settled resolution, so the Scope check failed and the verdict rule rejected the issue. The gold label for `issue-15` is also `reject`.

**Check rationale**

> | Scope | Issue body + ALL available comments + linked-PR evidence in the bundle | **FAIL** if the issue is an explicit umbrella/tracking issue; a pure usage/support request; maintainer-stated core-internals work; **or the thread/history contains repeated implementation attempts that ended in closed/unmerged PRs without a settled resolution**; **or the requested feature depends on an unresolved product/design decision that determines what should actually be implemented**. Otherwise **PASS** only if there is a single bounded objective with an actionable description or a concrete target with a defined expected result. A good-first-issue label does not override any Scope failure. **The grader must inspect the entire provided comment thread before assigning PASS.** | required |

The current Scope check was written this way so the skill does not accept an issue merely because its current wording looks small. It requires the complete issue thread and linked-PR history to show that the implementation target is actually settled and bounded.

**Trade-offs**

The quoted Scope check gives up some superficially small issues that might otherwise look like good first issues. In particular, it can reject an issue when the present request is short but the historical thread shows repeated implementation attempts that ended in closed or unmerged PRs without a settled resolution. That trade-off is intentional: the rubric favors a clearly actionable issue over a small-looking issue whose implementation is still unresolved.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

1. **The issue's fit to my interests and to the time available.**  
   I selected issue #73 because it is a bounded documentation/configuration consistency fix. The live run estimated it at 1–2 hours, so it fits the time available for a first contribution and is narrower than the other accepted candidates.

2. **What the verdict identified correctly, and what I weighed that the rubric could not.**  
   The verdict correctly identified #73 as accepted: it has no AI restriction, recent human maintainer activity, no visible existing claim, recent repository activity, and a single bounded objective. I also weighed the practical effort and the fact that this is a documentation-only change when choosing among the three accepted issues.

3. **The anticipated difficulty in claiming it.**  
   The live output reports no assignee, no linked PR, and zero comments for #73. There is therefore no visible existing claim in the evidence I checked. The remaining difficulty should be following the repository's claiming process when I carry the issue into Unit 2.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
