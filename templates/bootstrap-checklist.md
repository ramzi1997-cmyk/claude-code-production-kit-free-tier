# New-project bootstrap — 5 steps, ~10 minutes

Do these once, in order, before the first real build session. Every step exists
because skipping it costs more later than it saves now.

## 1. Write the project `CLAUDE.md` (3 min)

Copy [`CLAUDE.minimal.md`](CLAUDE.minimal.md) into the project and fill in the
brackets — especially **Non-negotiables** and **Do NOT**. If you can't state the
run/test commands yet, write "TBD" and fix it the moment they exist. An agent
without ground truth will invent its own.

## 2. Init git and commit immediately (1 min)

```
git init && git add -A && git commit -m "bootstrap"
```

Everything an agent does should be diffable against a known-good state. No git =
no undo = no honest review.

## 3. Create the test harness before the first feature (3 min)

One test file, one trivial passing test, one command that runs it. The point is
that `run the tests` exists on day one, so the first real feature can start with
a failing test (see [`tdd-loop`](../skills/tdd-loop.md)) instead of with an
excuse.

## 4. Decide what the agent may NOT do (2 min)

Fill the **Do NOT** list for real: production data files, directories that are
frozen, whether the agent commits or you do. Every disaster story starts with a
permission nobody remembered granting.

## 5. Plan the first feature before building it (variable)

Run [`plan-first`](../skills/plan-first.md) on feature #1, red-team the plan
([`red-team`](../skills/red-team.md)), freeze it to `docs/PLAN-<feature>.md`,
then build. The first feature sets the pattern for every session after it.

---
*From the free tier of the [Claude Code Production Kit](../README.md). The full
kit's version is an 8-step bootstrap with settings/permission templates and the
persistent memory architecture.*
