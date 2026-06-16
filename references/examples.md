# Examples: before / after

Each pair sets a failing answer against its calibrated version. Scenarios are generic.

## Example 1 — under-communicating (precise but unreadable)

Scenario: the user asks an agent to take stock of a paused code repository.

**Before (fact-dump by evidence type, no narrative, no "so what"):**

> Current branch feat/x, HEAD a1b2c3. ahead 6 / behind 0 vs upstream.
> RetryConfig default retries=0 (config.py:88). pytest 142 passed.
> Also a worktree feat/y, ahead 19, pytest 71 passed.

Every line is true and verifiable, but the reader has to assemble the story.

**After (organized by object, coordinates kept + a "so what" added):**

> **Bottom line**: two half-built feature lines, both local-only, never pushed (the biggest risk). Stock-take only; no files changed.
>
> **Feature X** (branch `feat/x`) — *finished, stopped one step before release*
> - Code wired up, tests green (`pytest → 142 passed`).
> - But retries are off by default (`config.py:88`, `retries=0`) — a single transient failure aborts the run, conflicting with "high availability."
> - 6 commits ahead of remote, never pushed (`ahead 6`) — loss risk is entirely local.
>
> **Feature Y** (worktree `feat/y`) — *baseline is stale*
> - Tests green (`pytest → 71 passed`).
> - Guess: baseline older than X — inferred from the branch point only, merge conflicts not actually tested.
>
> **Next step**: ① push both branches for backup; ② dig into X's finishing checklist; ③ assess Y's merge cost.

What changed: bottom line first; organized by the two features (objects), not by Git/tests/config; each number keeps its coordinate but gains a "so what"; the one inference wears a `guess` hat and says why it's unverified.

## Example 2 — over-packaging (fluent but saying too much)

**Before (fake coordinates, metaphor as assertion, forced tidiness):**

> X is 85% done, Y 95%. The author kept paying down tech debt and stopped before finishing. The two lines are cleanly one problem each.

The fault is not "giving a percentage" — it's **handing over felt numbers, unhatted, as if measured**: `85%/95%` look counted; "kept paying down debt" writes a guess as a statement; "cleanly one problem each" forces tidiness onto messy reality.

**After (estimate hatted and grounded, metaphor riding a fact, messiness owned):**

> X is roughly ~85% done (basis: code all wired, 14 dedicated tests passing, but the release flag and real-data regression aren't done yet — this is an estimate, not a measurement).
> Guess: the last 6 commits (`commit a1b2c3..f4e5d6`) all patch the same hand-off spot, which **looks like** repeatedly paying down one debt — this reads the commit pattern, it's not confirmed intent.
> The two lines are broadly independent, but I haven't tested for shared-module conflicts, so I won't claim "cleanly one problem each."

Note the after **keeps the ~85% estimate** — a rough estimate carries information and should stay; it's just marked as an estimate and given its basis. Calibration is not deleting the judgment; it's fitting the judgment with a hat proportional to the evidence.

## Example 3 — the collapse valve (don't over-structure a trivial answer)

User asks: "Which cache backend does this project use by default?"

**Before:** a full [Bottom line] [Overview] table [Verification] [Next step].

**After:** Redis by default (`config.py`, the `CACHE_BACKEND` default).

One sentence, one coordinate. The scaffold must match the weight of the content.

## Example 4 — discussion-mode honesty (dismantling the tidy structure you just built)

Mid-discussion, just after proposing a neat symmetric model.

**Before:** Right, exactly — cleanly one each, perfectly symmetric.

**After:** You've got a point — but let me take apart my own "perfect symmetry": reality isn't that even, each side actually carries a bit of the other's flaw, and that diagram trimmed the burrs to look clean.

Shows: uptake first ("you've got a point"), then actively dismantling an over-tidy structure rather than defending it because it reads well.
