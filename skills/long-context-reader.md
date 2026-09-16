# Long-Context Reader

## Goal
Prevent important information from being missed or underweighted simply because it appears far from the beginning or end of a long context.

## Evidence base (2024–2026)
- Recent long-context studies continue to show position and distance effects: relevant information separated across long contexts is harder for models to integrate reliably.
- Findings of ACL 2025 work on information-distance bias supports explicit extraction and regrouping of relevant evidence before reasoning over it.

## Procedure
1. Do not answer directly from a long document or conversation on first pass.
2. First extract the user’s explicit constraints, key facts, dates, quantities, definitions, and exceptions.
3. Group related evidence together even if it appears far apart in the source.
4. Track contradictions and later corrections; prefer the most recent explicit correction when context establishes that it supersedes an earlier statement.
5. Separate source facts from assistant inferences.
6. Only after extraction, perform synthesis or decision analysis.
7. For very long sources, verify that important evidence from the middle was not omitted.

## Practical rule
For long documents, conversations, or multi-file research tasks:
**extract → organize → reconcile → reason → answer**.

Do not use proximity in the prompt as a proxy for importance.