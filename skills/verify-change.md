# verify-change — drive it end-to-end; don't trust green tests

> Use before committing any nontrivial change to product code, especially right
> after tests go green.

## The pitch

Green tests answer "does the code do what the tests say it should." They do not
answer "can a real user actually reach this." Those are different claims, and the gap
between them is one of the most common ways solo-built software quietly ships broken:
every unit test passes, the agent reports success, and the feature is simply
unreachable from the actual UI or CLI a user touches. `verify-change` is the habit of
closing that gap yourself — run the thing, click the thing, look at the actual output
— before you consider a change done.

This is not "write more tests." It's "don't trust the summary; drive the flow."

## When to use it

- Right after [`tdd-loop`](tdd-loop.md) reports green, before you commit.
- Before committing any change to product source that has a runtime surface (i.e.
  almost anything except pure docs/test-only changes).
- Especially when a change spans layers (API + DB + UI) — that seam is exactly where
  "each layer's tests pass in isolation" hides an integration gap.

## Copy-paste implementation

```
The tests are green. Before I commit this, verify it actually works end-to-end:
1. Start the real app/service (not a test harness).
2. Drive the exact user-facing flow this change is supposed to affect — the real
   command, the real UI click path, the real API call a client would make.
3. Show me the actual output/response, not a description of what should happen.
4. If this touches persistence, restart the process and confirm the data survived —
   don't just check the in-memory state.
```

## Worked example

My statistics platform is the cautionary tale that makes this skill non-optional.
By the time six backend tasks were done — persistence, migrations, an event log,
assumption gating, a deepened advisor, effect sizes with confidence intervals —
**77 tests were green**. And yet the desktop GUI still called the old, non-persisted
endpoint: every one of those six tasks was API-only and **invisible to an actual
user of the app**, despite a fully green suite the whole time. Nobody lied; the
tests were testing the right thing at the wrong layer. Only a pass that actually
opened the GUI and ran the real flow caught that the shipped capability and the
reachable capability had quietly diverged.

The inverse also happened correctly on the same project: an earlier persistence fix
was verified with exactly this discipline — tests green **plus a live smoke test**
(restart the app, confirm the data survived, confirm the real user database was
untouched). That's the pattern to copy: tests plus one real run, every time.

## Warning label

- This assumes there's a real runtime surface to drive. Don't force this on changes
  that only touch tests or docs — there's nothing to observe, and the skill becomes
  theater.
- "I re-read the diff carefully" is not verification. The whole point is to exercise
  the running system, because that's the only way to catch layer-boundary gaps like
  the GUI example above.
- Verification is a main-thread habit, not something to fully delegate — a cheap
  subagent can build the feature, but "never trust a self-report" belongs to whoever
  is accountable for the change.

---
*From the free tier of the [Claude Code Production Kit](../README.md). The full kit
adds the cost playbook this pairs with (`cost-route`: cheap models build, frontier
models review).*
