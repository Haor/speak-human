# Report mode — one-way absorption

For delivering an artifact the reader understands in one pass: status reports, investigation findings, analyses, change summaries, explanations.

## Goal

The reader fully understands the artifact without follow-up questions. Success = a single artifact absorbed.

## The skeleton

```
[Bottom line]  one-line conclusion · boundary statement (what changed / what was NOT touched)

[Overview]     a scannable table OR 3–5 prioritized points — the whole picture in ~30 seconds

[Object A]     — one-line characterization
  · status:   <claim> (coordinate/number) — which means <so what>
  · blocker:  <claim> (coordinate)         — which means <so what>
  guess: <interpretation, hatted>

[Object B]     ... same shape

[Verification & boundary]
  · ran:       <full command → real result>
  · not done:  what wasn't actually run; what is only inferred
  · red line:  don't do X

[Next step]    2–3 numbered options; the decision stays with the user
```

**Organize the body by the object the user cares about** (a feature, a bug, a module), **never** by evidence type (Git / code / tests / docs). Evidence-type organization forces the reader to reassemble the story themselves — the number-one cause of "I can't follow this" (root cause in diagnosis.md).

## The communication-engineering toolkit

These add a layer, on top of correct facts, that makes the facts absorbable. **None costs precision** — the precise term/number stays verbatim in the parentheses. This layer is exactly what an under-communicated answer is missing.

| Technique | What to do |
|---|---|
| **Representation choice** | Fit the form to the data's shape. Many objects × many attributes → **a table**; a spectrum / two opposed poles → **an ASCII axis**; an ordered procedure → a numbered list; a relationship → a small diagram. **Don't flatten 2-D comparison data into 1-D bullets** — the comparison itself is the information. |
| **Jargon-lowering** | Lead with the human-readable action, precise term in parentheses: "switch to two-pass processing (the `mode` setting)," not a bare `mode="insert"`. |
| **Naming / handles** | Give recurring things a short handle and reuse it ("Object A," "fake coordinate") instead of repeating a long identifier each time. |
| **So what** | Give every number/fact a "— which means ___." A bare number is inert to an unfamiliar reader; `ahead 33 (33 local commits never pushed — biggest loss risk)` lands. |
| **Progressive disclosure** | Bottom line first, then detail, then judgment. Never open with a flat fact dump. |
| **Reader modeling** | Supply the premise the reader lacks. Before reporting an object's status, say in one line what it is. |
| **Metaphor for compression** | Use one image to compress a complex state — but it must ride on a fact, and if it touches intent/causation, wear a `guess:` hat. |

## Plain AND precise — the bridge

The apparent conflict dissolves through placement: **plain language in the main clause, precise coordinate in the parentheses.** They sit in different positions and don't fight.

- ✗ nerdy: `config.py:88 default retries=0`
- ✗ vague: it doesn't retry by default, a bit aggressive
- ✓ bridged: **by default it never retries (`config.py:88`, `retries=0`), so a single transient failure aborts the whole run — which conflicts with the stated "high availability" goal.**

## Pre-send gate (report mode)

1. Bottom line graspable in ~30 seconds?
2. Body organized by object, not by evidence type?
3. Every claim carries a coordinate or a hedge label?
4. Any fake coordinates (felt numbers posing as measured)?
5. Verified vs inferred — visibly separated?
6. Scaffold proportional to content (collapse if trivial)?
