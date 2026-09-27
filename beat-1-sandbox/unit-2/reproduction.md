# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

## Your identity upstream

**GitHub username**

Aayush7788

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73#issuecomment-5857773868

can i work on #73. I’m going to investigate the configuration mismatch between README.md and .env.example, reproduce the issue, and document what I find.

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s3/issues/73#issuecomment-5857822361

## Reproduction Report — Issue #73

## Environment

OS: Windows
Repository: Aayush7788/pathreview-ai301-fa26-s3
Repository state tested: 2f4e82f52efbcfcc57d65b3fa5348672163ca088

## Steps to Reproduce

1. Open `README.md` and check the Quick Start environment configuration.
2. Open `docs/SETUP.md` and check the environment configuration instructions.
3. Open `.env.example` and check the documented LLM provider options and API key variables.
4. Open `core/config.py` and check the LLM configuration fields.

## Expected Behavior

`README.md`, `docs/SETUP.md`, `.env.example`, and `core/config.py` should provide consistent instructions for configuring the supported LLM providers.

## Actual Behavior

`README.md` instructs users to add `OPENROUTER_API_KEY` to `.env`.

`docs/SETUP.md` also tells users to set `OPENROUTER_API_KEY` and describes it as required for AI features.

However, `.env.example` documents only `mock` and `openai` as LLM provider options and contains `OPENAI_API_KEY`, but does not contain `OPENROUTER_API_KEY`.

At the same time, `core/config.py` defines `openrouter_api_key`, `openrouter_base_url`, and `openrouter_model`.

## Evidence

Repository commit tested: `2f4e82f52efbcfcc57d65b3fa5348672163ca088`.

`README.md` contains the instruction to add `OPENROUTER_API_KEY` to `.env`.

`docs/SETUP.md` contains the instruction to set `OPENROUTER_API_KEY` and describes it as required for AI features.

`.env.example` contains:
`LLM_PROVIDER=mock`
`OPENAI_API_KEY=sk-your-key-here`

`.env.example` does not contain `OPENROUTER_API_KEY`.

`core/config.py` defines the OpenRouter configuration fields.

## Eval iterations

**Run history**

18/20

**Package analysis**

pkg-05: My rubric decided REJECT, while the gold label was ACCEPT. The disagreement came from the `steps-complete` check being too strict for this package.

**Check rationale**

> | steps-complete | Reproduction steps in the report | A stranger can follow the listed setup and commands from the stated starting point without guessing or relying on private/unshared files or configuration. | required |

I kept this check because the reproduction should be followable by another person and should not depend on private setup or missing information.

**Trade-offs**

The `steps-complete` check helps reject reproductions that another person cannot follow, but pkg-05 showed that making this check too strict can reject an otherwise acceptable package.
