# Error Localization

## Goal
Find the exact failing claim, assumption, calculation, or reasoning step before attempting a correction.

## Evidence base
Research from 2024 shows an important distinction: models can often repair an error once its location is known, even when they are poor at identifying the error location unaided.

Reference:
- LLMs cannot find reasoning errors, but can correct them given the error location, Findings of ACL 2024.

## Procedure
1. Break the answer or reasoning chain into discrete steps.
2. Test each step against the available evidence or constraints.
3. Identify the earliest point where the reasoning becomes unsupported or inconsistent.
4. Separate source error, interpretation error, arithmetic error, assumption error, and conclusion error.
5. Correct the smallest failing unit first.
6. Propagate the correction forward only where necessary.
7. Re-evaluate the conclusion after repair.

## Why this matters
Rewriting an entire answer after a vague instruction like “check this” can introduce new errors and hide the original failure. Local repair is usually easier to audit.

## Anti-patterns
Avoid:
- changing correct sections just because one claim failed;
- treating disagreement with the conclusion as proof that the reasoning is wrong;
- locating an error only by stylistic intuition;
- correcting downstream symptoms while leaving the upstream assumption unchanged.

## Output rule
When correction matters, be able to state internally: **what failed, where it failed, why it failed, and what changed.**