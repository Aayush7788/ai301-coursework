# Procedure: how this tool grades a PR package

## Read order

1. In live mode, read `scope.md` first; refuse if its Repo line is a placeholder or the issue/PR targets a different repository. Then read the issue and relevant thread, recording the reported and expected behavior plus explicit maintainer constraints. In eval mode, treat the bundle as the whole record and fetch nothing.
2. Read the accepted plan and its `## Deviations` section, then its repro context. Record the promised files, outcomes, tests, boundaries, and any honestly deferred work.
3. Read the PR title and description, then the full diff and commit summary. For live mode, obtain the committed branch change with `git diff main...HEAD`; do not count uncommitted files. For eval, use the bundle's diff and commits.
4. Read test evidence and compare each command/result with the plan's test plan and the reported issue behavior.
5. Read the repository PR template, contribution guide, explicit thread requests, and relevant policies. In eval, use only the bundle's repo-facts block and thread highlights. In live mode, also read `voice-guide.md` and note any title/description rule violations without changing the verdict unless the rubric covers them.

## Evidence gathering

1. For `issue-and-plan-fidelity`, list the issue's expected outcome, the plan's promised files and changes, its explicit boundary/deviations, and the actual changed files/hunks. Compare the description's fidelity claims with that list. Separate planned work intentionally deferred in a clear deviation from work silently omitted; do not mistake a useful, tested bounded slice for drift when both plan and description disclose it.
2. For `decisive-test-evidence`, list every material behavior/path named in the plan's test plan, the original repro, and the applicable repo-requested local checks. Locate the issue repro and relevant regression test or focused test output, then compare the observed result with the plan's expected result. A reproduced primary case plus a regression test may cover sibling variants when the diff shows the same fix shape applied to each; require separate evidence for variants with distinct behavior or implementation. A control alone, suite-only assertion without output, or unsupported "works" claim is not proof.
3. For `diff-reviewability`, inspect every changed hunk and the commit summary. Identify only unrelated changes or leftover debug/dead/commented experimental code and churn that materially hides the issue fix; name the file/hunk or artifact.
4. For `repository-standards`, enumerate explicit template sections and checklist asks, contribution-guide requirements, maintainer requests, and written AI-use requirements. Match each applicable ask to the description, diff, or evidence. Do not invent standards absent from those sources; CI that runs only after PR creation is not a pre-open local result.
5. For `description-evidence-alignment`, compare factual claims with the delivered diff and actual test output, including any stated shortfall, deferral, or CI status. Quote a claim and its supporting or contradicting artifact.
6. In live mode, compare the title and description with each concrete voice-guide rule and report specific violations in the readable summary.

## Check execution

1. Grade every rubric row once, in table order. Use `pass` only when its stated outcome is supported, `fail` when observed evidence contradicts it, and `unclear` when required evidence is genuinely absent or insufficient.
2. For missing or failed commands, report the exact unavailable/failing result and reason if present. Do not convert an honestly reported failure into a pass; assess whether the evidence still verifies the issue-specific change and whether the repository requires that check to pass.
3. Do not invent issue facts, file changes, test outputs, repo requirements, AI policies, or maintainer direction. When sources conflict, cite both and apply the written pass condition.
4. Give each grade one concise evidence line containing the deciding quote or observable file/result. Avoid grading style, length, headings, or commit count unless a written repository requirement makes it relevant.

## Verdict assembly

1. Apply the rubric's verdict rule exactly: accept only if all required checks pass; any required fail or unclear means reject. Preferred checks never gate readiness.
2. Emit exactly one result for every rubric check, retaining its exact name and the grade/evidence.
3. Return only `accept` or `reject` as the verdict. End with a valid fenced JSON block matching `CONTRACT.md` exactly; the JSON block is the final content.
