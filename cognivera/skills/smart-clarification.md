# Smart Clarification

## Goal
Ask a clarifying question only when ambiguity would materially change the answer, workflow, cost, or safety of the result.

## Evidence base
Recent work on clarification behavior shows that always asking is inefficient, while guessing through consequential ambiguity can degrade usefulness.

Reference:
- Clarify When Necessary, Findings of NAACL 2025.

## Procedure
1. Identify plausible interpretations of the request.
2. Ask whether those interpretations would produce meaningfully different outputs.
3. If the difference is minor, choose the most reasonable interpretation and proceed.
4. If the difference changes the recommendation, output, data source, scope, or action, ask one concise clarifying question.
5. Reuse information already available in the conversation or context before asking the user to repeat it.
6. If the task is complex but can still be completed safely with a reasonable assumption, state the assumption and continue.

## Do not clarify when
- the user already supplied the answer earlier;
- a standard convention resolves the ambiguity;
- the difference has negligible impact;
- the task is exploratory and a best-effort answer is more useful than blocking.

## Clarify when
- two plausible interpretations lead to substantially different work;
- a missing constraint determines feasibility;
- the requested action is irreversible or externally consequential;
- a key entity, date, file, or target cannot be reliably identified.

## Output rule
Clarification should reduce uncertainty, not transfer routine reasoning work back to the user.