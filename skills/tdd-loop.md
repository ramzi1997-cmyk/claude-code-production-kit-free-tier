# tdd-loop — make the agent write the failing test first

> Use when starting a new module, fixing a bug (regression test first), or any
> time you want a safety net that isn't "trust the summary."

## The pitch

Agents self-report. Left alone, "I implemented the feature and it works" means the
agent believes it, not that it's true. Test-driven development is the cheapest fix
for that: a failing test written *before* the implementation is a claim you can check
mechanically, and a green test afterward is evidence instead of a vibe. The order
matters — write the test first, watch it fail for the right reason, then implement.
If you let the agent write code and tests together, you get tests that describe
whatever the code happens to do, which catch nothing.

## When to use it

- Starting any new module or non-trivial function — write the test(s) before the
  implementation exists.
- Fixing a bug — the regression test that reproduces the bug comes first, so you have
  proof the fix actually fixes it and proof it won't silently regress later.
- Anywhere you'd otherwise be tempted to just read the diff and trust it "looks
  right."
- Skip it for pure exploration/prototyping code you intend to throw away.

## Copy-paste implementation

Three explicit turns, don't collapse them into one prompt:

**1. Red.**
```
Write a failing test for <behavior>. Do not write any implementation code.
Run it and show me it fails for the right reason (not an import error or typo).
```

**2. Green.**
```
Now write the minimum code to make that test pass. Don't add anything the test
doesn't require yet. Run the full suite, not just the new test.
```

**3. Refactor.**
```
The test is green. Now clean up the implementation without changing behavior —
run the suite again after every change to confirm it stays green.
```

Never let the agent skip straight to green — "write the test and the code together"
collapses the one guarantee TDD gives you.

## Worked example

My Windows system-monitoring CLI's first real commit is literally titled test-first:
*"Domain model + epistemics contract, test-first (17 tests)."* The domain model and
its contracts were pinned down by tests before any Windows-probe implementation
existed, and the suite grew from there — 41 tests green by the time the process
probe with signature verification shipped.

My statistics platform takes the discipline a step further, and it's worth stealing:
the stats engine is checked against a **pure-NumPy oracle** — an independent,
hand-verified reference implementation the suite compares results against, not just
"does the function return without throwing." That's TDD applied to correctness of a
*result*, not just presence of a *feature*. When you're building something where "it
ran" and "it computed the right number" are different claims (statistics, billing,
scoring), the oracle pattern is the right escalation.

## Warning label

- This assumes the test can actually fail meaningfully before the implementation
  exists — a test that passes trivially isn't testing anything. Always look at the
  red step; don't skip past it.
- TDD does not replace [`verify-change`](verify-change.md). Green tests plus a
  feature nobody can reach from the UI is a real failure mode — see that skill's
  worked example for what it looks like when it happens.
- Batch TDD passes into one session/brief per feature rather than one test per
  message — a cold agent re-derives context on every spawn, so tiny back-and-forth
  turns burn tokens for no quality gain.

---
*From the free tier of the [Claude Code Production Kit](../README.md).*
