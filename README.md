**English** · [中文](README.zh-CN.md)

# speak-human

> *"Speak human."* (说人话)

[![skills.sh](https://skills.sh/b/Haor/speak-human)](https://skills.sh/Haor/speak-human)

An [Agent Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills) that gives any AI agent a single communication discipline: **speak like a human, while staying honest** — make every substantive answer both readable and honestly anchored.

Different agents (and different models) drift into opposite failure modes. Some are precise but unreadable — raw fact-dumps, branch names and line numbers with no narrative, nothing telling you what any of it *means*. Others are fluent but over-confident — tidy dichotomies, vivid metaphors, and felt numbers like "~85% done" presented as if they were measured. `speak-human` names both failures, traces each to its root cause, and pulls answers toward the calibrated middle.

## The one rule

> **Calibration** — say exactly as much, and exactly as confidently, as the evidence supports; package it just enough to be understood, no more.

```
  EXPRESSION < EVIDENCE          EXPRESSION = EVIDENCE          EXPRESSION > EVIDENCE
   under-communicating              TARGET                        over-packaging
   true, but unreadable      as much said as understood,     fluent, but not all true
                             as much understood as evidenced
```

It constrains the *alignment between what you say and what you actually know* — not your style — so the same discipline works across agents and models.

## What's inside

| File | What it covers |
|---|---|
| `SKILL.md` | The core: the calibration rule, the four invariants, the coordinate table, the two brakes, the scenario dial, the collapse valve, and the pre-send gate. |
| `references/diagnosis.md` | *Why* answers fail — the curse of knowledge, the sentence-skeleton difference, fluency that launders guesses — and how to prevent each. |
| `references/report-mode.md` | One-way absorption: the report skeleton + the communication-engineering toolkit. |
| `references/discussion-mode.md` | Two-way convergence: the moves that only matter in multi-turn dialogue. |
| `references/examples.md` | Before/after rewrites for each failure mode. |

## Core ideas

- **Four invariants** every answer carries — Intent, Action, Findings, Coordinates.
- **Organize by object, not by evidence type.** Reporting "Git / code / tests / docs" forces the reader to reassemble the story. Report by the feature/bug/module they care about, and fold the coordinates in.
- **Honest coordinates, generalized.** Every sentence either points to something checkable (`file:line`, a real command + result, an exact ref) or wears a hedge label (`guess:` / `unverified`). A guess's coordinate is admitting it's a guess.
- **Two brakes.** If you under-communicate, add the communication layer (the facts stay; only packaging is added). If you over-package, cut or hat what exceeds the evidence — but keep useful estimates; just give them a hat.
- **Two modes.** *Report* optimizes absorption; *discussion* optimizes convergence and adds its own moves (uptake, shared vocabulary, increment-then-checkpoint).

## Installation

### With the `skills` CLI (recommended)

```bash
npx skills add Haor/speak-human
```

Works with Claude Code, Codex, Cursor, and 70+ other agents — the CLI auto-detects which you have installed. Use `-g` for a global install, or `-a <agent>` to target a specific one (e.g. `-a claude-code`).

### Manually

```bash
# global (available in every project)
git clone https://github.com/Haor/speak-human ~/.claude/skills/speak-human
```

The skill triggers automatically when an answer is a substantive report, analysis, or status round-up, or when it feels hard to follow or too slick. You can also invoke it by name ("speak human" / "说人话").

## License

MIT — see [LICENSE](LICENSE).
