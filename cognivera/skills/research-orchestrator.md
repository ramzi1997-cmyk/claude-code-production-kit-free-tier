# Research Orchestrator

## Goal
Select the smallest useful combination of quality-control skills for each task instead of applying every technique to every answer.

## Core principle
Better AI behavior comes from routing the task through the right process, not from blindly adding more reasoning steps.

## Routing procedure
1. Identify the task type: factual lookup, analysis, research synthesis, long-context reading, writing, decision support, or technical work.
2. Decide whether clarification would materially change the answer.
3. Decide whether current or external evidence is required.
4. For long or source-heavy tasks, extract the relevant evidence before drafting.
5. Build an initial answer or working hypothesis.
6. Identify the claims or steps most likely to fail.
7. Verify those claims with external evidence when possible.
8. Localize any error before rewriting the surrounding answer.
9. Calibrate confidence to the quality and completeness of the evidence.
10. Apply a human-oriented writing pass only after factual and reasoning issues are resolved.

## Skill selection
Use only what the task needs.

### Simple factual question
Usually:
- direct answer;
- evidence lookup if freshness matters;
- calibrated uncertainty when evidence is incomplete.

### Research-heavy question
Usually:
- smart clarification when ambiguity is consequential;
- long-context reader;
- evidence-first verification;
- claim-level factuality;
- error localization;
- calibrated uncertainty;
- human-writing variance.

### Long document or conversation
Usually:
- long-context reader first;
- claim-level factuality if the result is factual;
- human-writing variance for the final presentation.

### Writing task
Usually:
- human-writing variance;
- factuality and verification modules only when the text makes external factual claims.

## Stop rule
Do not add more verification or reasoning passes when they are unlikely to change the answer materially.

## Final quality gate
Before responding, ask:
- Did I answer the actual request?
- Are the central factual claims supported?
- Did I preserve uncertainty where evidence is incomplete?
- Did I avoid unnecessary complexity?
- Is the final response readable by a human rather than merely structurally complete?
