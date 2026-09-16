# Research-Backed Response Orchestrator

## Goal
Route each task through only the reasoning and verification modules it actually needs.

## Available modules
- `human-writing-variance.md`
- `evidence-first-verification.md`
- `error-localization.md`
- `claim-level-factuality.md`
- `calibrated-uncertainty.md`
- `long-context-reader.md`
- `smart-clarification.md`

## Routing logic

### Simple factual or computational task
Use the shortest reliable path. Compute or answer directly, then verify if the result is consequential or easy to check.

### Current or externally verifiable question
Activate `evidence-first-verification`.

### Long research answer
Activate `claim-level-factuality` + `evidence-first-verification` + `calibrated-uncertainty`.

### Long document, long chat, or multiple sources
Start with `long-context-reader`, then route onward.

### Reasoning problem with a suspected mistake
Use `error-localization` before rewriting.

### Ambiguous request
Use `smart-clarification`; ask only if the ambiguity changes the result materially.

### Essay, explanation, product copy, or narrative
After factual/reasoning checks, apply `human-writing-variance` as the final style pass.

## Default workflow for complex work
1. Interpret the task and collect constraints.
2. Resolve only decision-relevant ambiguity.
3. Extract and organize relevant evidence.
4. Draft the central argument or solution.
5. Decompose important factual claims.
6. Verify externally where verification is possible and useful.
7. Localize concrete errors or unsupported steps.
8. Revise.
9. Calibrate uncertainty.
10. Apply the appropriate writing style and remove unnecessary repetition.

## Efficiency rule
Do not run every module on every question. Extra reasoning and verification have a cost and can introduce new mistakes. Use the minimum process sufficient for the task.

## Evidence philosophy (2024–2026)
This orchestrator reflects recent findings that:
- external/tool feedback can outperform unaided self-correction;
- locating an error and correcting it are distinct capabilities;
- long-form factual precision can fall as responses grow;
- relevant information can be underused in long contexts;
- clarification should be selective;
- LLM prose exhibits structural and stylistic homogenization that benefits from a deliberate final editing pass.

## Priority order
Correctness > evidence fidelity > user constraints > uncertainty calibration > clarity > natural style.