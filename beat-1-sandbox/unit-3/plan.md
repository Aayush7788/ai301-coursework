# Plan: Issue #73 — README and `.env.example` OpenRouter key mismatch

Issue: https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73
Reproduction: my posted Windows report at repository state `2f4e82f52efbcfcc57d65b3fa5348672163ca088`.

## Diagnosis

The setup docs tell me to add `OPENROUTER_API_KEY`, but copying `.env.example` creates a file with only `LLM_PROVIDER=mock` and `OPENAI_API_KEY`. My reproduction explicitly found `OPENROUTER_API_KEY` absent from the copied example. `core/config.py` defines the `openrouter_api_key`, `openrouter_base_url`, and `openrouter_model` settings, so the example omits a setting the setup instructions reference.

The reproduction does not show that the application can select or use OpenRouter at runtime. A repository search finds the provider setting declarations in `core/config.py` but no runtime use of `llm_provider` or the OpenRouter fields. I will not claim that this change enables that behavior.

## Scope

In scope: add an `OPENROUTER_API_KEY` placeholder and a short explanatory comment to `.env.example`, alongside the existing LLM key setting. Preserve `LLM_PROVIDER=mock`, its current options comment, and `OPENAI_API_KEY`.

Not in scope: changes to `README.md`, `docs/SETUP.md`, `core/config.py`, provider selection or runtime behavior, other environment variables, and unrelated cleanup. I will not list `openrouter` as a supported `LLM_PROVIDER` value because the current code does not establish that it is supported.

## Files

- `.env.example` — add the missing key placeholder and explain its relation to the setup instructions.

## Approach

1. Add an `OPENROUTER_API_KEY` placeholder beside the existing `OPENAI_API_KEY` in the LLM configuration section.
2. Keep the mock default and existing provider options intact; do not imply this change wires an OpenRouter client.
3. Review the diff to confirm it changes only the missing example configuration.

## Test plan

Before: my posted reproduction reported that `.env.example` did not contain `OPENROUTER_API_KEY`. Before editing, I checked the original file from the branch's base with `git show 2f4e82f52efbcfcc57d65b3fa5348672163ca088:.env.example`; it showed `LLM_PROVIDER=mock` and `OPENAI_API_KEY=sk-your-key-here`, then reported `OPENROUTER_API_KEY not found in .env`.

After: copy `.env.example` to a temporary file and run:

```powershell
$tempEnv = [System.IO.Path]::Combine($env:TEMP, ('pathreview-73-' + [guid]::NewGuid().ToString('N') + '.env'))
Copy-Item -LiteralPath '.env.example' -Destination $tempEnv
Get-Content -LiteralPath $tempEnv | Select-String -Pattern '^(LLM_PROVIDER|OPENAI_API_KEY|OPENROUTER_API_KEY)='
Remove-Item -LiteralPath $tempEnv
```

Expected: all three variables appear; `LLM_PROVIDER` remains `mock`, the OpenAI placeholder remains unchanged, and the new OpenRouter placeholder is present. I verified the setup docs still mention the key and ran `git diff --check`. This checks the reported example-file mismatch; it does not test runtime OpenRouter support.

Observed after: the copied file contained all three variables with the expected values above, and `git diff --check` passed.

## Risks and unknowns

The repository's current code does not show whether OpenRouter is an active provider, despite the configuration fields and setup instructions. This documentation-only change exposes the key the docs already request but does not promise the provider is selectable or functional. If the issue owner intended provider selection to change too, that needs confirmation and a separate implementation plan.

## Deviations

The build followed the plan: I changed only `.env.example` and did not alter provider selection or runtime behavior.
