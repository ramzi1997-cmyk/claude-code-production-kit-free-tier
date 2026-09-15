# Evidence-First Verification

## Goal
Do not treat an internally plausible answer as verified. Use external evidence or task-appropriate tools whenever the claim can be checked.

## Evidence base (2024–2026)
- Gou et al., **ICLR 2024**, *CRITIC: Large Language Models Can Self-Correct with Tool-Interactive Critiquing*: tool-based feedback improved correction across QA, code, and other tasks, underscoring the value of external validation. https://proceedings.iclr.cc/paper_files/paper/2024/hash/fef126561bbf9d4467dbb8d27334b8fe-Abstract-Conference.html
- Kamoi et al., **TACL 2024**, *When Can LLMs Actually Correct Their Own Mistakes?*: prompted self-feedback alone is unreliable in general; reliable external feedback is a key condition for successful correction. https://aclanthology.org/2024.tacl-1.78/
- Han, Buntine & Shareghi, **Findings of EMNLP 2025**, *VerifiAgent*: combines meta-verification with adaptive tool-based verification across reasoning types. https://aclanthology.org/2025.findings-emnlp.891/
- DeVerna et al., **Findings of ACL 2026**, *Large Language Models Require Curated Context for Reliable Political Fact-Checking—Even with Reasoning and Web Search*: curated evidence substantially outperformed unstructured reliance on model reasoning/search in that fact-checking setting. https://aclanthology.org/2026.findings-acl.1467/

## Procedure
1. Draft the answer or hypothesis.
2. Mark claims that are current, numerical, externally verifiable, consequential, surprising, or uncertain.
3. Choose the best verifier for each claim: source search, primary document, calculator, code execution, database, file, or direct observation.
4. Verify claims independently of the wording used in the draft when possible.
5. Prefer primary and authoritative evidence over summaries.
6. If sources conflict, represent the conflict instead of forcing false certainty.
7. Revise only after evidence is collected.
8. Keep unsupported claims out of the final answer or clearly label them as inference/uncertainty.

## Do not
- Use “I checked my reasoning” as a substitute for evidence.
- Treat multiple repetitions of the same model answer as independent proof.
- Search indiscriminately when the answer is already directly computable or contained in a trusted supplied source.

## Output rule
For high-stakes or research-heavy work, the final response should make it possible to distinguish **source-backed facts**, **reasoned inference**, and **remaining uncertainty**.