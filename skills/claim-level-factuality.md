# Claim-Level Factuality

## Goal
Make long answers more reliable by checking factual claims at the claim level instead of judging the response as one block.

## Evidence base (2024–2026)
- Zhao et al., Findings of ACL 2025, “How Does Response Length Affect Long-Form Factuality”: longer answers showed lower factual precision, largely associated with exhaustion of reliable facts. https://aclanthology.org/2025.findings-acl.161/
- Wan et al., Findings of EMNLP 2025, “FaStFact”: improves long-form factuality evaluation through claim extraction, pre-verification, evidence collection, and verification. https://aclanthology.org/2025.findings-emnlp.1295/
- Liu et al., EMNLP 2025, “VeriFact”: emphasizes refined fact extraction and preserving context during verification. https://aclanthology.org/2025.emnlp-main.905/
- Carnerero-Cano et al., ACL 2026, “FactCorrector”: structured factual feedback improves post-hoc correction of long-form answers. https://aclanthology.org/2026.acl-long.2147/

## Procedure
1. Before expanding an answer, decide how much factual detail is actually useful.
2. Split important factual content into atomic or near-atomic claims.
3. Preserve the context needed to interpret each claim; do not verify misleading fragments in isolation.
4. Prioritize checks for claims that are current, numerical, surprising, disputed, or central to the conclusion.
5. Retrieve evidence for those claims and record whether each is supported, contradicted, or unresolved.
6. Remove unnecessary claims that add length without improving the answer.
7. Revise contradicted claims and soften unresolved claims.
8. Recheck whether the final conclusion still follows after correction.

## Density rule
More detail is not automatically better. Stop adding factual assertions when additional detail no longer improves the user’s decision or understanding.

## Output rule
For research-heavy answers, prefer fewer well-supported claims over a longer response padded with low-confidence facts.