# red-team — attack your plan before it costs you a build-week

> Use after `plan-first` drafts a plan and before you start building, or whenever
> a decision is expensive to reverse.

## The pitch

A plan you wrote yourself is the plan you're least equipped to find holes in — you
already believe it, so you read past its weak points. Red-teaming means deliberately
switching seats: stop being the author and become the harshest informed critic you
can be, *before* the plan costs you a week of build time instead of ten minutes of
thinking.

## When to use it

- Immediately after [`plan-first`](plan-first.md) produces a draft, before you
  freeze it.
- Before any decision that's expensive to reverse: architecture choice, pricing,
  positioning, a "we'll never need X" assumption.
- When something has been true in your head for a while and nobody has challenged it
  recently.

## Copy-paste implementation

```
Red-team this plan/decision: <paste plan or describe decision>.

Attack it from every angle:
1. Market/competitive reality — has someone already solved this for free or cheaper?
   What changed recently that I might not know about?
2. Hidden assumptions — what am I taking for granted that might not be true?
3. Failure modes — what's the most likely way this quietly fails, not dramatically
   fails?
4. Cost I'm underestimating — time, maintenance, reputational, legal.
5. What would make a smart, skeptical outsider dismiss this in one sentence?

Don't soften it and don't stop at the first issue — find as many as you can, then
rank them by how much they change the decision.
```

Do this as a genuinely separate pass — a fresh context or a sub-agent with no
investment in the plan being good tends to find more than the same thread that wrote
it, because it isn't anchored on its own prior reasoning.

## Worked example

The paid version of this very kit got red-teamed on the day it was specced, and the
result changed the plan materially. The red team surfaced that Anthropic runs a
**free** official plugin marketplace with 55+ curated plugins, and that community
mega-lists (36k+ stars) already give components away — a fact the original plan had
not weighed. The plan didn't get scrapped; it got sharpened: positioning moved from
"skills+hooks pack" to "the discipline layer," pricing assumptions were re-checked,
and the kill criteria tightened. Same day, before a single wasted build-week.

The harsher version of the same discipline, applied to a whole portfolio: a
red-team-style diagnosis of my own projects found **3+ codebases in flight with zero
paying customers** — and it produced physical consequences (`FROZEN.md` markers
placed in every non-active repo), not just a paragraph of caveats.

## Warning label

- A red team that never changes anything is theater. If ten red-team passes in a row
  all conclude "looks fine," you're either genuinely disciplined or not actually
  attacking the plan — check which.
- This assumes you can tolerate hearing "this is weaker than you think" without
  re-litigating the critique. The value is in acting on the findings, not in
  generating a list that gets filed and ignored.

---
*From the free tier of the [Claude Code Production Kit](../README.md). The full kit
adds `premortem` (narrative failure-path analysis) and `scope-guard` (the narrower
"should I even be building this right now" check).*
