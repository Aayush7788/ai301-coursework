# Unit 4 — Test and Submit

## Your pull request

**Pull request**

https://github.com/codepath/pathreview-ai301-fa26-s3/pull/158

**Branch**

`docs/73-openrouter-env-example`

## Eval iterations

**Run history**

1. Full run: 17/20 agreed. `decisive-test-evidence` was too strict for three clear accepts (`pkg-02`, `pkg-05`, `pkg-13`).
2. I started a seven-package partial run while diagnosing the rule, but it stalled before returning scores and was interrupted; it wrote no result.
3. Partial run `--only pkg-02,pkg-05,pkg-13,pkg-01,pkg-03,pkg-04,pkg-12`: 7/7 agreed. The three former misses passed; the four canaries remained rejects.
4. Final full run: 19/20 agreed; all categories had at least one match. `pkg-20` was the only disagreement. This matches the final `eval-run.txt`.

**Package analysis**

`pkg-20`: my rubric returned **accept**; the gold label is **reject**. Its repo facts state that Ghostty requires AI disclosure, including the tool and extent of assistance, while the candidate description contains no AI-use disclosure. The `repository-standards` check did not make that specific disclosure requirement salient enough, so the grader missed the standards-wall signal. This is the final run's one disagreement.

**Check rationale**

> “When the plan names closely related variants implemented with the same fix shape, a reproduced primary case and a regression test covering that shared behavior can establish coverage if the diff shows each variant received the fix; do not demand a separate repro for every variant.”

I added this sentence to `decisive-test-evidence` after the first run rejected three clear accepts whose primary repro and regression coverage established the shared fix. The seven-package partial run rechecked all three and included a canary from each category; it scored 7/7 before the final full run.

**Trade-offs**

The revised test rule allows representative evidence for sibling paths with the same fix shape. That changed the verdicts for `pkg-02`, `pkg-05`, and `pkg-13` from reject to accept, matching gold. The `--only` canaries `pkg-01`, `pkg-03`, `pkg-04`, and `pkg-12` stayed reject. The remaining `pkg-20` miss shows the cost: repository-specific AI disclosure requirements need more explicit wording in the standards check.

