# Unit 3 — Plan and Build

## Posted upstream

**GitHub username**

Aayush7788

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73#issuecomment-5979687302

My Windows repro on #73 showed that after copying `.env.example`, the file had `LLM_PROVIDER=mock` and `OPENAI_API_KEY`, but no `OPENROUTER_API_KEY`. The README and setup guide tell users to configure that key, and `core/config.py` defines the OpenRouter settings.

I plan to add the missing key placeholder to `.env.example` only. I’ll keep the mock default and current provider options unchanged: the repository code does not show that OpenRouter is selectable at runtime, so this plan does not claim to enable it. I’ll repeat the copy-and-check steps from my repro and confirm the new key appears while the existing values stay the same.

## Your branch

**Branch**

docs/73-openrouter-env-example

**Evidence**

Before, at base commit `2f4e82f52efbcfcc57d65b3fa5348672163ca088`:

```powershell
git show 2f4e82f52efbcfcc57d65b3fa5348672163ca088:.env.example | Select-String -Pattern '^(LLM_PROVIDER|OPENAI_API_KEY|OPENROUTER_API_KEY)='
if (-not (git show 2f4e82f52efbcfcc57d65b3fa5348672163ca088:.env.example | Select-String -Pattern '^OPENROUTER_API_KEY=' -Quiet)) { Write-Output 'OPENROUTER_API_KEY not found in copied .env' }
```

```text
LLM_PROVIDER=mock
OPENAI_API_KEY=sk-your-key-here
OPENROUTER_API_KEY not found in copied .env
```

After, copying the changed file to a temporary `.env`:

```powershell
$tempEnv = Join-Path $env:TEMP ('pathreview-73-after-' + [guid]::NewGuid().ToString('N') + '.env')
Copy-Item -LiteralPath .env.example -Destination $tempEnv
Get-Content -LiteralPath $tempEnv | Select-String -Pattern '^(LLM_PROVIDER|OPENAI_API_KEY|OPENROUTER_API_KEY)='
Remove-Item -LiteralPath $tempEnv
git diff --check
```

```text
LLM_PROVIDER=mock
OPENAI_API_KEY=sk-your-key-here
OPENROUTER_API_KEY=sk-or-v1-your-key-here
git diff --check: passed
```

## Eval iterations

**Run history**

- First attempt: stopped at a Python `UnicodeEncodeError` before grading; no score was produced.
- Second attempt: `0/0` with all 20 items errored because Claude Code was signed out; no eval file was written.
- Successful full run: `20/20` (PASS). Category matches: clear-accept 7/7, scope-creep 4/4, thread-convention 2/2, unbuildable 3/3, wrong-cause 4/4. This matches the saved `eval-run.txt`.

**Package analysis**

`pkg-20`: our rubric decided REJECT, matching the gold REJECT. The repo facts require disclosing all AI use, including the tool and extent of assistance. The candidate plan comment contains no AI-use disclosure, so `thread-and-conventions` holds it despite the otherwise strong, bounded plan.

**Check rationale**

> | thread-and-conventions | Candidate plan comment read against Thread highlights, repo facts/policies, and the Candidate plan | The comment reflects any explicit maintainer constraint or request that affects the work, follows stated communication requirements (including AI disclosure when required), accurately summarizes the plan, and makes no promise absent from it. Fail for a material conflict or omitted explicit requirement, not silence about incidental details. | required |

This check covers the two thread-and-convention failure modes in the eval: ignoring an explicit maintainer direction and omitting a repository-required AI disclosure. The run matched both packages in that category.

**Trade-offs**

The check focuses on explicit maintainer requests and written repository policies, so it may miss a subtle preference that is only implied. That limit avoids treating incidental comments or classmates' plans as requirements; the full run still matched both thread-and-convention packages.
