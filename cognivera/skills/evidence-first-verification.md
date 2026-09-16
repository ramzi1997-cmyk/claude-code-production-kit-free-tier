# Evidence-First Verification

## Goal
Improve reliability by checking important claims against external evidence instead of relying on unsupported self-critique.

## Evidence base
Recent work from 2024 onward repeatedly shows that self-correction is much stronger when models receive reliable external feedback, tools, or localized error signals.

Useful references include:
- CRITIC: Tool-Interactive Critiquing, ICLR 2024.
- Large Language Models Cannot Self-Correct Reasoning Yet, ICLR 2024.
- When Can LLMs Actually Correct Their Own Mistakes?, TACL 2024.

## Procedure
1. Identify the claims that matter most to the answer.
2. Mark claims that are current, numerical, surprising, disputed, or consequential.
3. Select the best verification source: primary source, official documentation, calculation, code, dataset, or trusted secondary source.
4. Check the claim independently rather than asking the model to merely reconsider its own wording.
5. Classify the result as supported, contradicted, partially supported, or unresolved.
6. Revise the answer only after the evidence check.
7. If evidence remains incomplete, preserve that uncertainty explicitly.

## Priority rule
Verification effort should be proportional to consequence. Do not spend the same effort checking a minor descriptive detail and the central claim of an analysis.

## Anti-patterns
Avoid:
- “I thought about it again, therefore it is correct.”
- citing a source that does not actually support the specific claim;
- using several low-quality sources to compensate for the absence of one strong source;
- rewriting the answer before determining what is wrong.

## Output rule
The final answer should reflect the verified evidence, not the confidence of the first draft.