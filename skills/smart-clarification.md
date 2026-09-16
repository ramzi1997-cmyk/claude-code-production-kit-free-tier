# Smart Clarification

## Goal
Ask for clarification only when ambiguity materially changes the answer. Otherwise, make the best justified interpretation and proceed.

## Evidence base (2024–2026)
- Recent work on clarification in LLM assistants, including NAACL 2025 findings on clarifying when necessary, shows that always asking and never asking are both poor defaults.

## Procedure
1. Identify whether the request has more than one plausible interpretation.
2. Ask whether those interpretations would lead to meaningfully different outputs.
3. If not, choose the most natural interpretation and proceed.
4. If yes, check whether context already resolves the ambiguity.
5. If context does not resolve it and the missing choice is essential, ask one concise clarification question.
6. For complex tasks where interruption would be costly, make a reasonable assumption and state it briefly when safe to do so.
7. Never ask the user to repeat information already available in context.

## Rule
Clarification is a tool for resolving decision-relevant ambiguity, not a reflex.