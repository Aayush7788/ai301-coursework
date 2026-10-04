# Procedure: how this skill grades a plan package

## Read order

1. In eval mode, treat the bundle as the entire record and do not fetch outside information. In live mode, read `scope.md` first; stop if its repo line is unfilled or the issue is outside scope.
2. Read the issue and relevant thread comments so the requested behavior and explicit maintainer direction are clear.
3. Read the reproduction report and referenced artifacts before the plan. Record the actual result, expected result, controls, and any observed stage that supports or rules out a cause.
4. Read the candidate plan in order: Diagnosis, Scope, Files, Approach, Test plan, Risks/Unknowns, then read the plan comment. Grade only what these drafts state and quote.
5. In live mode, read applicable repo contribution/AI policies and `voice-guide.md`. In eval mode, use only the bundle's repo facts; ignore `scope.md` and the voice guide.

## Evidence gathering

1. For `diagnosis-grounded`, quote the diagnosis and the repro observations or controls that support or contradict it. Do not treat a reporter's or thread participant's suspected cause as established if the repro disproves it.
2. For `issue-fit` and `bounded-scope`, record the issue's reported and expected behavior, the in-scope outcome, the explicit boundary, and any extra work. Check whether each extra task is needed; preserve a useful, testable, honestly deferred slice.
3. For `executable-approach`, note the files/areas and actual steps. Identify basic design choices left for the implementer to invent.
4. For `decisive-test`, record the setup, inputs, runnable check, expected observable result, and its link to the original repro. Note whether a focused automated regression test is applicable; otherwise identify the explicit equivalent check. A suite-only promise is not a fix-specific result.
5. For `thread-and-conventions`, compare the comment with explicit maintainer requests/constraints and the repository's stated communication and AI disclosure rules. Record the signal and the matching or conflicting text; ignore incidental thread details.
6. For `risks-and-unknowns`, record only stated uncertainties, limits, and deferrals, then compare certainty claims with those limits and the repro evidence.
7. In live mode only, compare the draft comment with each concrete `voice-guide.md` rule. Mention a violation in the readable summary; it changes the verdict only if a rubric check also covers it.

## Check execution

1. Grade the checks once, in this order: diagnosis-grounded, issue-fit, bounded-scope, executable-approach, decisive-test, thread-and-conventions, risks-and-unknowns.
2. Assign `pass` only when the pass condition is supported, `fail` when evidence contradicts it, and `unclear` when evidence is absent or insufficient. Missing evidence is unclear, not proof of a defect; required unclear grades hold.
3. Do not invent a cause, file, command, expected result, policy, risk, or maintainer preference absent from the package. If sources conflict, cite the conflict and apply the written pass condition.
4. Give every grade a short quote or precise observable fact from the plan/comment or comparator. State what is missing when a condition is only partly met.

## Verdict assembly

1. Apply the rubric: accept only if every required check passes; any required fail or unclear means reject. Preferred grades never change the verdict.
2. Emit one result for each rubric check, retaining its exact name and a concise evidence line that identifies the deciding quote or comparison.
3. Use `accept` or `reject` in the final fenced JSON block, with the issue URL or bundle id as `item`. Ensure the JSON is valid and is the final content.
