# Evidence Guide: where evidence lives in a plan package

## Diagnosis and grounding

### Where it lives
In an eval bundle, compare `Candidate plan > Diagnosis` with `Issue` and `Repro evidence`, especially actual results, controls, and intermediate observations. In live mode, use the issue description, the student's posted repro, and thread observations the repro confirms.

### What good looks like
The proposed cause explains the specific failure and survives the repro controls. A control that still fails with the suspected component disabled, or evidence showing the failure before the named stage, weighs against that cause.

## Scope

### Where it lives
Use `Candidate plan > Scope`, `Files`, and `Approach`, compared with the issue request and material thread direction. In live mode, use those sections in `plan.md` and the issue thread.

### What good looks like
The plan names its boundary and what it leaves alone; the files and steps fit within it. Extra work has evidence it is needed. A useful, testable smaller slice can pass when it clearly says what it defers and why.

## Executability

### Where it lives
Use `Candidate plan > Files` and `Approach`, including step order, and relevant repo facts. In live mode, use `plan.md` and documented repository conventions/layout where available.

### What good looks like
A contributor can begin in the named places and follow the selected approach without choosing the basic design for the author. Concise steps are enough; investigation with no chosen direction is not executable.

## Test plan

### Where it lives
Use `Candidate plan > Test plan` and compare setup, inputs, and expected output with `Repro evidence`. In live mode, compare `plan.md` with the student's posted repro and the documented test framework or command where relevant.

### What good looks like
The check exercises the reported behavior on the real code and names an observable expected result. Use a focused automated regression test when applicable; for documentation-only or otherwise non-automatable changes, an explicit consistency or manual check can be decisive. A full suite with no fix-specific result is not decisive.

## Honesty

### Where it lives
Use `Candidate plan > Risks/Unknowns`, explicit deferrals in `Scope`, and certainty claims in the diagnosis, approach, and comment. Compare them with open questions and limitations in the issue and repro. In live mode, record a build deviation under `## Deviations` in the updated plan.

### What good looks like
The plan distinguishes evidence from assumptions and names meaningful limits or deferrals. It does not claim certainty the package contradicts. Do not invent unknowns just because the plan is brief.

## Comms

### Where it lives
In eval, compare `Candidate plan comment` with `Thread highlights`, `Repo facts` (including contribution and AI policies), and the plan. In live mode, use the issue thread, repository contribution/AI instructions, and draft comment. Check `voice-guide.md` in live mode only.

### What good looks like
The comment addresses relevant explicit maintainer direction and accurately describes the plan. It follows stated disclosure rules and does not promise a deadline or work the plan does not contain. Ignoring a direct constraint or required disclosure fails; omitting incidental thread details does not.
