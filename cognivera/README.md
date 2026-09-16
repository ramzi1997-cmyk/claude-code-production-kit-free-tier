> [!WARNING]
> **Historical working title — not a cleared brand or product launch.** An external trademark listing reports an EU registration for “Cognivera” (application 019354380, registered 13 August 2026) covering overlapping AI/software activities, and others also use this name. The record has not been independently confirmed in the official EUIPO register. Do not market, register, or release this work under that name pending a proper clearance check. These early AI-assisted Markdown drafts are a research prototype, not a validated reliability improvement. A separate, neutrally titled release candidate is being prepared; no open-source licence has been selected for that candidate.

# Cognivera (archived working-title documentation)

**Evidence-first skills for better AI reasoning, verification and writing.**

This early prototype is a modular instruction layer for AI systems researching, verifying, handling long context, expressing uncertainty and writing for human readers. It is not a trained AI model and no performance gains have been established.

## Original motivation

- Overconfident answers without strong evidence.
- Self-correction without external feedback.
- Unsupported details in excessively long answers.
- Missed constraints in long contexts.
- Overused clarification questions.
- Formulaic writing and excessive explanation.

## Architecture

Request → interpret → retrieve relevant evidence → draft → audit critical claims → locate errors → revise → communicate uncertainty → edit for readability.

An orchestrator selects only the skills a given task needs; simple requests should not trigger the complete pipeline.

## Prototype modules

- `research-orchestrator.md`: selects relevant modules.
- `evidence-first-verification.md`: checks important assertions against external evidence.
- `error-localization.md`: isolates faulty steps before repairing them.
- `claim-level-factuality.md`: audits individual factual claims.
- `calibrated-uncertainty.md`: aligns confidence language with evidence.
- `long-context-reader.md`: reconstructs scattered context and tracks corrections.
- `smart-clarification.md`: asks only consequential questions.
- `human-writing-variance.md`: improves stylistic variety without sacrificing accuracy.

## Research and release status

This documentation draws on selected publications from 2024–2026, including peer-reviewed papers and preprints. Findings may not generalize to all models and contexts. The existing files are early Markdown prototypes; a standards-compliant version must use skill directories containing `SKILL.md` with proper metadata, and benchmarks should be run before claims about quality.

The project was initiated by Ramzi Souiki with AI-assisted drafting. Account ownership and repository history alone do not prove exclusive intellectual-property rights; methods from cited studies remain those of their respective researchers. The original branding proposal is withdrawn pending name clearance.
