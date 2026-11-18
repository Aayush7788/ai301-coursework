# Improving my pull request review assistant

## Overview

I built and improved `pr-precheck`, a rubric-driven AI assistant that checks whether a pull request is ready to submit. It compares an issue and plan with the code change, test evidence, and repository rules, then returns an `accept` or `reject` verdict with evidence. My first full evaluation agreed with the expected labels on 17 of 20 cases. I changed one evidence rule, retested it, and reached 19 of 20 on the final run. One missed repository disclosure rule still shows where the assistant needs work.

## What happened

I wanted the assistant to make a careful, evidence-based decision about a pull request, rather than approve it because its description sounded confident. I wrote a rubric with five required checks: issue and plan fidelity, test evidence, diff reviewability, repository standards, and description-to-evidence alignment. The assistant reads the package and cites a fact for each check before giving its verdict.

My first full evaluation agreed with the expected answers on 17 of 20 packages. Three clear accepts, `pkg-02`, `pkg-05`, and `pkg-13`, were rejected. I reviewed their evidence and saw the same pattern: each plan named related variants with the same fix shape, one main case had been reproduced, and a regression test covered that shared behavior. My rubric demanded separate reproduction evidence for every variant. That rule was stricter than the evidence needed to verify those changes.

I changed `decisive-test-evidence` to allow a reproduced main case and a shared regression test when the diff shows that each related variant received the same fix. The rule I added says:

> “When the plan names closely related variants implemented with the same fix shape, a reproduced primary case and a regression test covering that shared behavior can establish coverage if the diff shows each variant received the fix; do not demand a separate repro for every variant.”

I then ran a seven-package evaluation with the three previous misses and four reject cases as checks against overcorrecting the rubric. It agreed on all seven. The three false rejects became accepts, and the four canary rejects stayed rejects. The final full evaluation agreed on 19 of 20 packages, above the 18-of-20 passing bar. These are saved evaluation results from my course work, not a claim that the assistant has been validated on every pull request.

One miss remained. On `pkg-20`, the assistant said `accept`, while the expected answer was `reject`. The repository facts required an AI-use disclosure, but the candidate description did not include one. My `repository-standards` rubric mentions AI disclosure when a repository requires it, yet the assistant did not make this specific rule decisive. That result showed me that broad standards wording was not enough for every repository-specific policy.

I also submitted my own change in the course repository as [PR #160](https://github.com/codepath/pathreview-ai301-fa26-s3/pull/160), which GitHub reported with all five CI checks passing. That PR is separate from the saved evaluation above: the evaluation is what exposed and verified the rubric change.

## Limitations and what's next

The final run still had one false accept. The assistant can miss a repository-specific policy even when its rubric names that policy type. The evaluation covers 20 packages, so 19 of 20 does not prove that the tool is reliable on every project or every kind of pull request.

Next, I would make the standards check quote each relevant repository rule and compare it directly with the candidate description. I would add a case for the missing AI-use disclosure, confirm that it rejects the package, and rerun the full evaluation to make sure the change does not create new false rejects. That would make the assistant's reasoning easier to check and its limits clearer.
