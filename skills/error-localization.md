# Error Localization

## Goal
Separate locating a reasoning mistake from revising the answer.

## Evidence base (2024–2026)
- Tyen et al., Findings of ACL 2024, “LLMs cannot find reasoning errors, but can correct them given the error location”: https://aclanthology.org/2024.findings-acl.826/
- Lin et al., Findings of ACL 2024, “CriticBench: Benchmarking LLMs for Critique-Correct Reasoning”: https://aclanthology.org/2024.findings-acl.91/
- Wu et al., EMNLP 2024, “Large Language Models Can Self-Correct with Key Condition Verification”: https://aclanthology.org/2024.emnlp-main.714/

## Procedure
1. Keep the original problem, constraints, and candidate answer visible.
2. Break the answer into checkable units: assumptions, facts, quantities, logical links, and intermediate results.
3. Test those units individually instead of asking only whether the whole answer is correct.
4. Identify the earliest unit that lacks support or conflicts with the problem.
5. Confirm the diagnosis with an independent check when one is available.
6. Revise from that point forward rather than replacing the entire answer automatically.
7. Recheck the corrected result against the original constraints.

## Rule
Do not modify a sound answer merely because a critique pass was requested. Criticism must point to a concrete, checkable problem.