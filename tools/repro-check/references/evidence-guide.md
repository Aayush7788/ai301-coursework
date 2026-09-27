# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

# Evidence Guide

## Environment

### Where it lives
The `Environment:` line at the top of the repro report. Compare it with the issue's stated environment and the commands or artifacts used during reproduction.

### What good looks like
It records the tool or application version, OS, relevant framework or toolchain, and commit or release when applicable. If the tested version differs from the issue's version, the report clearly says so.

## Steps

### Where it lives
The reproduction steps in the repro report, including setup, input, commands, and any required configuration.

### What good looks like
A stranger can follow the steps from the stated starting point without guessing. The steps use the issue's relevant command and input and do not depend on private or unshared files, configuration, or environment.

## Behavior shown

### Where it lives
The actual output, terminal log, screenshot, or other artifact in the repro report, read against the behavior described by the issue.

### What good looks like
The observed behavior directly matches the issue's reported behavior. Check the actual error, output, exit code, or visible behavior rather than assuming that any failure reproduces the issue.

## Honesty

### Where it lives
The claim, expected/actual section, and reproduction result in the report.

### What good looks like
The report says what the evidence supports. A reproduced issue is supported by the observed behavior. A cannot-reproduce result is acceptable when the attempted steps, environment, and evidence are stated clearly. Do not treat a different error or behavior as a reproduction.

## Comms

### Where it lives
The claim comment and repro comment, together with the repository's contribution and AI-use policy.

### What good looks like
The claim names the specific issue and what will be done next without promising a fix or deadline. The repro comment states the observed result accurately and follows repository-specific communication requirements, including required AI disclosure.

## Artifact

### Where it lives
The output excerpt, terminal log, screenshot, video, or other attached evidence referenced by the repro report.

### What good looks like
The artifact is evidence for the specific issue behavior being claimed. Its contents, such as an error message, output, or exit code, can be checked directly against the issue description.

## Claim-specific

### Where it lives
The claim comment and the claim-related statements in the repro report.

### What good looks like
The claim identifies the issue-specific behavior and relevant version or context. It does not claim a cause, reproduction, or certainty that the available evidence does not establish.
