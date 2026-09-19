# Rubric: is this a good first issue?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| AI policy | `CONTRIBUTING.md`; any AI/agent policy it directly links to; eval: `contribution policy` in Repo facts | **pass** if AI-generated code/documentation is allowed, including disclosure/review/testing/understanding, or no AI restriction is stated. **fail** if relevant AI-generated code/documentation is prohibited. **unclear** if a referenced policy does not answer this. | `required` |
| Maintainer alive | Last 5 default-branch commits and authors; ignore bot-only commits | **pass** if at least one human maintainer commit is within 90 days of capture date/today. **fail** if none. **unclear** if dates/authors are missing. | `required` |
| Scope | Issue body + ALL available comments + linked-PR evidence in the bundle | **FAIL** if the issue is an explicit umbrella/tracking issue; a pure usage/support request; maintainer-stated core-internals work; **or the thread/history contains repeated implementation attempts that ended in closed/unmerged PRs without a settled resolution**; **or the requested feature depends on an unresolved product/design decision that determines what should actually be implemented**. Otherwise **PASS** only if there is a single bounded objective with an actionable description or a concrete target with a defined expected result. A good-first-issue label does not override any Scope failure. **The grader must inspect the entire provided comment thread before assigning PASS.** | `required` |
| Already being worked on | Assignee, Development/linked PRs, comment thread | **fail** if an assignee exists, an open linked PR exists, or a recent explicit claim comment exists. In live Path Review, ignore classmates' claim comments per `scope.md`. **pass** if none exist. Closed-unmerged PRs or stale claims alone do not fail. **unclear** if the evidence cannot determine the current status. | `required` |
| Repository active/in use | Latest release, last push/commit activity, archived flag | **pass** if not archived AND a release or meaningful commit activity exists within 90 days of capture date/today. **fail** if archived OR neither exists within 90 days. **unclear** if required evidence is missing. | `required` |
| Maintainer response | Live: maintainer first-response sample from `references/evidence-guide.md`; eval: `maintainer first-response sample` in Repo facts | **pass** if the available sample shows timely maintainer responsiveness according to the evidence guide. **fail** only if the available evidence clearly shows a lack of maintainer responsiveness. **unclear** if the sample is insufficient to determine responsiveness. This is a **preferred** check and does not by itself determine the verdict. | `preferred` |

## Verdict rule

Accept only if **every required check is `pass`**.

Any `fail` or `unclear` on a required check means `reject`.

Preferred checks do **not** gate the verdict. They are used only to help rank or distinguish issues that already pass all required checks.