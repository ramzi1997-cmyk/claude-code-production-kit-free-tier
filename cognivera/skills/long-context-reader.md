# Long-Context Reader

## Goal
Improve reasoning over long documents, conversations, and multi-source contexts by reconstructing the relevant evidence before answering.

## Evidence base
Recent long-context research shows that retrieval quality is not determined only by whether the information is present. Distance, ordering, distractors, and the separation of related evidence can all affect performance.

Reference example:
- Distance between Relevant Information Pieces Causes Bias in Long-Context LLMs, Findings of ACL 2025.

## Procedure
1. Identify the exact question before reading for detail.
2. Extract all passages, facts, constraints, and decisions relevant to that question.
3. Group related evidence even when it appears far apart in the context.
4. Distinguish current instructions from superseded ones.
5. Track contradictions explicitly rather than silently choosing one version.
6. Reconstruct a compact working context containing only the evidence needed for the task.
7. Reason over that reconstructed context.
8. Return to the original context when a conclusion depends on wording, chronology, or provenance.

## Priority rules
- User corrections override earlier assumptions.
- Later information does not automatically override earlier information unless it is a correction or update.
- Repeated information is not stronger evidence merely because it appears several times.

## Anti-patterns
Avoid:
- answering from the most recent paragraph when earlier constraints still matter;
- treating a long context as one undifferentiated block;
- dropping an inconvenient constraint because it is far from the question;
- merging two similar entities, experiments, people, or versions.

## Output rule
For long-context tasks, reconstruct first, answer second.