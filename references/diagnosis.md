# Diagnosis: why answers become unreadable, and why they become over-packaged

Each failure direction has a root cause. Understand the cause and you can prevent it at the source instead of patching it after the fact.

## 1. Why under-communicating happens: the curse of knowledge + egocentric representation

An agent that has just done a pile of work has those symbols — branch names, line numbers, counts, abbreviations — **highly activated and self-evidently meaningful in its own head.** So it writes straight from its own activation state, never transposing into "does the reader hold this map?"

This is the **curse of knowledge**: once you know something, it's hard to imagine how it looks to someone who doesn't. It surfaces as **egocentric representation** — reporting from the "I" frame instead of the "you" frame.

> Every "speak human" technique is one move unfolded: **perspective-taking.** Under-communicating is not poor prose; it's a missing perspective shift.

## 2. The sentence skeleton: where the two writing styles diverge

Drop both styles to the grammar level and the difference is concrete:

**Under-communicating sentence = noun phrase + coordinate**

> `Current branch vs upstream: ahead 33 / behind 3. The 3 missing commits are 4ab4062 squash...`

- Subjects and connectives dropped; numbers and coordinates stacked.
- Extremely dense, and 100% verifiable.
- But it **assumes the reader already holds the map.** To someone without the context, `ahead 33` is a number with no "so what."

**Readable sentence = subject-verb-object + judgment + connective tissue**

> "33 local commits are ahead of upstream and have never been pushed (`ahead 33`) — meaning these changes exist only on your machine, the single biggest loss risk."

- Has a subject, connectives, a "you," a "which means."
- **Every sentence tells you how to interpret the previous one.**

> Key: readability is not bought by **dropping precision** — it's bought by **adding connective tissue** (subjects, connectives, "so what"). That tissue is exactly what the dense style omits, and exactly what the unfamiliar reader needs most.

## 3. How to prevent under-communicating

There is one core move: **before sending, simulate a reader without your context and ask, for each sentence, whether they can catch it.** Concretely (full toolkit in report-mode.md):

1. **Give every coordinate a "so what."** `ahead 33` → `ahead 33 (33 local commits never pushed — biggest backup risk)`.
2. **Lower the jargon.** Lead with the human-readable action, precise term in parentheses: `switched to two-pass processing (the mode setting)`, not a bare `mode="insert"`.
3. **Name recurring things.** Give them a short handle and reuse it instead of repeating a long identifier.
4. **Global before detail.** Bottom line first; never open with a flat fact dump.
5. **Supply the missing premise.** Before reporting an object's status, say in one line what it is.

**None of these costs precision** — the precise term/number stays verbatim in the parentheses; you only add a layer that makes the fact absorbable. That layer is what the under-communicated answer lacks.

## 4. Why over-packaging happens: fluency launders guesses into facts

The opposite failure is sneakier. **The very act of generating fluent text tricks you into feeling you "know."** A vivid metaphor, a tidy dichotomy, a confident causal chain all *read* like conclusions — but may just be fluent.

And over-packaging is **more dangerous** than under-communicating: nerd-speak visibly looks "undigested," so the reader stays wary; fluent, confident prose *invites trust* — the hallucination arrives sugar-coated.

It manufactures certainty the agent does not actually possess. The classic four:

- **Fake coordinates:** a felt number like `~85% complete` set next to real measurements, posing as one.
- **Metaphor overreach:** a guess about intent/causation written as a flat statement.
- **Lossy simplification:** dropping a load-bearing detail, so a reader who acts on it acts wrong.
- **Forced structure:** imposing a tidy dichotomy/table on messy reality, trimming away the real burrs.

## 5. How to prevent over-packaging

Mirroring the five brakes in SKILL.md, the core self-check is one line:

> **The smoother the phrasing, the more worth asking again: "is this true, or just fluent?"**

Concretely: a number must be measured or labeled an estimate (and keep useful estimates — just hat them); a metaphor must ride on a fact and wear a hat; a simplification must pass the action-lossless test; behavior claims require reading the code or an "unverified"; if reality is messy, say it's messy.

## 6. Both sides are one axis

```
  EXPRESSION < EVIDENCE             EXPRESSION = EVIDENCE             EXPRESSION > EVIDENCE
  UNDER-COMMUNICATING                TARGET (middle)                   OVER-PACKAGING
  goods are real, won't          as much said as understood,        speaks human, but says
  speak human                    as much understood as evidenced    things it never checked
  cause: curse of knowledge                                         cause: fluency laundering guesses
```

> Cure under-communicating: **the evidence is already there — add the expression** (perspective shift + toolkit).
> Cure over-packaging: **the expression is already there — cut or hat what exceeds it** (the five brakes).
> Opposite directions, same midpoint — **calibration.**
