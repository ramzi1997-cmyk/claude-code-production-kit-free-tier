# Claude Code Production Kit — Free Tier

Four battle-tested skills and two templates that turn Claude Code from "chatting
with an AI" into running a disciplined production line. Free, MIT-licensed, no
signup, no tracking. Clone it, pick one skill, try it on your next feature.

## Why this exists

I run several real projects with Claude Code — a statistics platform for
biologists, a Windows system-monitoring CLI, and the paid version of this kit
itself. Early on, my process looked like most people's: open a session, describe
a feature, accept whatever came out. It produced code fast and products slowly.
The low point: I discovered the **same product existed as four parallel
codebases** on my machine, because every fresh session rebuilt from scratch
instead of extending a trunk. All tests green, nothing shipped.

What fixed it wasn't a smarter model. It was process: plans that exist *before*
code, deliberate attacks on my own ideas, and never trusting an agent's
self-reported success. This repo is the smallest useful subset of that system.

## Three things that changed everything

**1. Plan before building.** A plan turns "the agent decided" into "I decided,
the agent executed." My statistics platform's architecture was written, scored
against its own rubric, and reviewed *as a document* before any code — and every
later build session pointed at that frozen file instead of improvising. The
four-forks disaster above is what the absence of this looks like.
→ [`skills/plan-first.md`](skills/plan-first.md)

**2. Red-team your own ideas.** The first version of the paid kit got red-teamed
on the day it was specced. The red team found that free community mega-lists and
an official plugin marketplace already gave away components — a fact the plan
hadn't weighed. The product got repositioned the same day, before a single
wasted build-week. Ten minutes of deliberate attack beat a month of wishful
building. → [`skills/red-team.md`](skills/red-team.md)

**3. Verify end-to-end — never trust the summary.** At one point my statistics
app had **77 green tests** across six completed backend tasks… and the desktop
GUI still called the old, non-persisted endpoint. Every feature was real, tested,
and *unreachable by an actual user*. Green tests answer "does the code do what
the tests say," not "can a user reach this." Drive the real flow before you call
anything done. → [`skills/verify-change.md`](skills/verify-change.md)

Bonus: [`skills/tdd-loop.md`](skills/tdd-loop.md) — red-green-refactor with an
agent, including the oracle-test pattern for code where "it ran" and "it computed
the right number" are different claims.

## What's in the box

```
skills/
  plan-first.md      # freeze a plan before the first line of code
  red-team.md        # attack your plan before it costs you a build-week
  verify-change.md   # drive the real flow; don't trust green tests alone
  tdd-loop.md        # make the agent write the failing test first
templates/
  CLAUDE.minimal.md        # a minimal project CLAUDE.md to copy and fill in
  bootstrap-checklist.md   # 5 steps to a sane new-project setup
```

## How to use this

1. Clone or download this repo.
2. Read **one** skill — start with `plan-first`.
3. Use its copy-paste prompt on your very next non-trivial feature.
4. Add `templates/CLAUDE.minimal.md` to a project as `.claude/CLAUDE.md`.
5. Iterate. The skills compose: plan → red-team → build (TDD) → verify.

## Want the full system?

The paid **Claude Code Production Kit** is the complete operating system this
was extracted from: **15 skills** (including diff review, incident review,
scope-guard, dependency vetting, memory consolidation), a **persistent memory
architecture**, **5 guardrail hooks** with stdlib-only Python implementations
(test gate, dangerous-command block, cost guard…), the **cost playbook** (route
~80–90% of work to cheap models, reserve frontier models for review), production
checklists, and a cross-platform installer.

Landing page: *(link coming at launch — watch this repo)*

## Questions?

Open an issue here, or find me on r/ClaudeAI. If one of these skills saves you a
rebuild, a star helps other people find this.

— SANAD
