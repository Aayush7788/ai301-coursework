# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| env-recorded | Environment line in the repro report | The report records the tool/app version, OS, relevant framework/toolchain, and commit or release being tested when applicable. | required |
| steps-complete | Reproduction steps in the report | A stranger can follow the listed setup and commands from the stated starting point without guessing or relying on private/unshared files or configuration. | required |
| behavior-matches | Output/log/artifact read against the issue description | The observed behavior matches the specific behavior reported by the issue, not merely a different error, failure, or adjacent symptom. | required |
| actual-expected | Expected and actual sections in the report | The report explicitly states both the expected behavior from the issue and the actual observed behavior, and they describe the same test. | required |
| claim-specific | Claim/comment and repro report | The claim identifies the issue-specific behavior/version and does not assert reproduction, cause, or certainty that the evidence does not support. | required |
| honesty-outcome | Claim and reproduction evidence | A reproduced issue is supported by evidence; a cannot-reproduce result is stated honestly with the attempted environment/steps and evidence. A confident claim of reproduction with different behavior fails. | required |
| artifact | Attached or embedded output, log, screenshot, or other reproducible evidence | The artifact directly shows the reported behavior or the relevant cannot-reproduce result. | preferred |
| conventions | Repository contribution/AI policy and the submitted comment | The submission follows repository-specific contribution requirements, including required AI disclosure or other required communication conventions. | required |

## Verdict rule

READY only if every required check passes. A preferred check may be absent without causing rejection. Any FAIL or UNCLEAR on a required check makes the verdict REJECT.
