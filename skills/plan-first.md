# plan-first — sketch a plan, freeze it, build to it

> Use before starting any feature that touches more than one file, changes a
> data model, or that you'd be annoyed to redo.

## The pitch

The single biggest difference between people who "vibe" with Claude Code and people
who ship is whether a plan exists *before* the first line of code. Without one, every
session becomes an improvisation: the agent makes a hundred small architectural
decisions inline, none of them reviewed, and by the time something looks wrong you've
built three more features on top of it. A plan turns "the agent decided" into "I
decided, the agent executed" — and it gives you (and any reviewer) a fixed point to
check the finished work against later.

This is not "write a spec for everything." A one-line bug fix doesn't need a plan. A
new module, a schema change, a cross-cutting refactor, or anything you'd hate to redo
does.

## When to use it

- Before any change that touches more than one file or crosses a layer boundary
  (API + DB + UI).
- Before adopting a new architecture pattern, even a small one.
- Whenever you notice you're about to say "let's just start and see how it goes."
- NOT for one-line fixes, typo corrections, or copy changes — the overhead isn't
  worth it and you'll train yourself to skip the skill entirely out of annoyance.

## Copy-paste implementation

Run this as an explicit two-step conversation, not one prompt:

**Step 1 — draft the plan.** Ask Claude for a plan, not code:

```
Draft a plan for <feature>. Do not write any code yet. Include:
1. The problem in one paragraph — what's broken or missing today.
2. The proposed change — files touched, new files, data/schema changes.
3. What you are explicitly NOT doing (non-goals).
4. Open questions you need me to answer before building.
Stop after the plan. Wait for my review.
```

**Step 2 — freeze it.** Once you're satisfied (after a [`red-team`](red-team.md)
pass — it composes with this skill, don't skip it), say so explicitly and have the
plan written to a file the build session can point at:

```
Write this plan to docs/PLAN-<feature>.md as the frozen baseline. Build against
this file. If you discover mid-build that the plan is wrong, stop and tell me
instead of silently deviating.
```

That last sentence is the part people skip and the part that matters — it converts
silent scope drift into a visible checkpoint.

## Worked example

A real project of mine (a statistics platform for biologists) took plan-first to
its logical extreme: a full architecture design was written, scored against its own
rubric (9.3/10, with the residual explicitly attributed to unproven claims), and
reviewed across multiple passes *before* implementation started. The owner approved
a **document**, not code. Only then did a charter authorize "Task 1." Later build
sessions tracked execution against that frozen roadmap task by task — which is only
possible because the plan was written down instead of living in someone's head.

Contrast this with what happened *without* a frozen plan: the same product ended up
as **three diverged forks** on one machine, because each cold AI session rebuilt
from scratch. No canonical plan meant no canonical anything.

## Warning label

- This assumes you (or a reviewer) actually read the plan before approving it.
  "Looks good" without reading is worse than no plan — it's a plan nobody checked.
- Freezing a plan is not the same as never changing it. The rule is: deviations get
  *surfaced*, not silently absorbed. One of my builds deviated from a plan directive
  (custom migrations instead of Alembic) — that's fine, because it was logged as a
  deviation with a stated trigger for reversal, not buried.
- Don't let planning become its own form of procrastination. If you're on your third
  planning pass with no code written, move to building.

---
*From the free tier of the [Claude Code Production Kit](../README.md). The full kit
adds `review-my-diff` (check the finished work against the frozen plan) and
`premortem` (assume it already failed — why?).*
