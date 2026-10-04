# Rubric: is this plan ready to post and build from?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here (via your procedure.md). It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the plan's scope statement, the test plan read against
     the repro evidence's steps, the plan comment read against the
     thread highlights, the repo-facts block) or a location from your
     references/evidence-guide.md. "The plan" is not a source; "the
     plan's stated cause read against what the repro evidence shows"
     is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (is
     this one bounded change? could a stranger start executing it?),
     never the write-up's shape (how many sections it has, how long it
     is, whether it uses headings). Structure-shaped checks are what
     make graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad plans posted. The lecture named the
failure families: the diagnosis ignores or contradicts the reproduced
evidence, the change is unbounded (scope creep), the plan targets the
symptom while the evidence points at the cause, a stranger could not
start executing it, the test plan proves nothing observable, the
unknowns are dressed up as certainty, and the comment ignores what the
thread or the repo's stated conventions ask. A rubric that ignores a
family will fail eval packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| diagnosis-grounded | Candidate plan's Diagnosis read against the issue's reported behavior and the Repro evidence, including controls and intermediate observations | The proposed cause explains the behavior the reproduction actually isolates. Pass when no quoted control or observed stage rules the cause out; fail when the plan repeats a disproved thread theory or targets a symptom the evidence separates from the cause. | required |
| issue-fit | Issue's requested/expected behavior and Candidate plan's Scope, Approach, and Test plan | The in-scope change would directly address the issue's reported behavior and produce its expected result. A clearly identified subproblem may be deferred when the plan says what is deferred and the chosen slice is independently useful and testable. | required |
| bounded-scope | Candidate plan's in-scope and not-in-scope statements, Files, and Approach, compared with the issue and material thread direction | The proposed work is limited to the issue-relevant change and its necessary validation. Fail for unrelated rewrites, migrations, options, or cleanup without issue or maintainer evidence that they are needed. Do not fail a smaller, explicitly bounded plan solely because it defers other issue work. | required |
| executable-approach | Candidate plan's Files and ordered Approach | A contributor can identify relevant files/areas and begin the described change without choosing its basic design or investigating what the plan leaves undecided. Concrete steps may be concise; vague exploration with no chosen direction fails. | required |
| decisive-test | Candidate plan's Test plan read against the Repro evidence and its observable output | The plan gives a runnable check of the reported behavior on the real code and states a concrete expected result after the change. A focused automated regression test is preferred when it adds repeatable coverage; a concrete replay of a narrow repro can also be decisive. For documentation/config examples or behavior that cannot be automated, an equivalent explicit check is acceptable. “Run the suite” alone fails. | required |
| thread-and-conventions | Candidate plan comment read against Thread highlights, repo facts/policies, and the Candidate plan | The comment reflects any explicit maintainer constraint or request that affects the work, follows stated communication requirements (including AI disclosure when required), accurately summarizes the plan, and makes no promise absent from it. Fail for a material conflict or omitted explicit requirement, not silence about incidental details. | required |
| risks-and-unknowns | Candidate plan's Risks/Unknowns and stated deferrals, read against the Repro evidence and Approach | Material unresolved assumptions, platform limits, or deferred behavior are stated plainly; certainty is not contradicted by the package. Missing detail is unclear, not an invented risk. | preferred |

## Verdict rule

Accept (ready) only when every required check passes. A fail or unclear
on any required check means reject (hold). Preferred checks add feedback
but never change the verdict. Treat unclear as fail for required checks;
for a preferred check, report unclear and leave the verdict unchanged.
