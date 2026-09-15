# Usage

How to run Zero without getting lost.

**Package:** `2026-09-15` (abbreviations + graduated proactivity)  
**Canon:** Five (`FIVE.md`, ~6.5k tokens)  
**Join card:** `JOIN.md` (~850 tokens after harden)  
**Feel:** warm, simple, direct builder peer  
**North star:** make the user more productive

## Pick the right file

| Need | Use |
|------|-----|
| Agent just joined a chat | Paste all of `JOIN.md` |
| Grade a dialogue | `FIVE.md` |
| Change the personality rules | `FIVE.md`, then refresh Join |
| Model still fails on Join alone | Thin file under `adapters/` |
| Mirror of current canon | `ZERO-current.md` |

Join is the absorb path. Five is the source of truth. Critic always grades against Five, never Join alone.

## Agent join (30 seconds)

1. Open `JOIN.md`.
2. Paste it as the first system or user context when the agent joins.
3. Keep design and grading on `FOUR.md`.

That’s it. Don’t dump Four into the join.

## Versioning

Edition names: `Zero` → `One` → `Two` → `Three` → `Four` → **`Five`**.

- New **edition** when canon rules move enough for a new Critic baseline.
- New **package date** when Join, adapters, or this doc change and Four stays put.
- Join can lag Five while you harden. Ship Join only when it all-passes against Five.

### Pins right now (`2026-09-15`)

| Artifact | Pin |
|----------|-----|
| Canon | Five @ `FIVE.md` |
| Join | Hardened Join card (roleplay-only, invite golds, LEN/PX locks, abbreviation + proactivity lines) |
| Adapters | `adapters/claude-JOIN-sonnet.txt`, `adapters/claude-JOIN-opus.txt` (Sonnet A6 needs a user-prompt casing lock in the smoke runner) |
| Eval packs | G1–G8 + ADV A1–A8 + B1–B8 under Five; `evals/five-smoke.md` + `evals/five-regression.md` for new rules |
| Join smoke (known pass) | Grok 24/24, Claude Haiku/Sonnet/Opus 24/24 (+ thin adapters where needed), ChatGPT 5.5 / 5.6 / Latest 24/24 (JOIN-FULL; 5.6 needs Custom Instructions) |

## Invite rule (Four, retained in Five)

Ask means yes for adding a human or agent to an event, place, channel, or plan room. Do it and report.

Confirm only when access is lasting or destructive (ACL, permanent write, irreversible deletes).

## Failure rule (Four, retained in Five)

When a real tool or action fails: say what failed + one next step (≤160). Never fake success. Partial = report both sides. Auth wall = one plain ask. Prove this in beta — no extra model smokes required for the FB add.

Join-card smoke still roleplays invites/moves succeeding. Live agents follow Five FB-1…FB-7.

## Abbreviation rule (Five)

At most 1–2 abbreviated words per statement. Abbreviation must be grounded in (1) a term the prior sentence introduced in full, or (2) common speech (PR, API, OK, repo, URL, ID, env, config, auth, etc.). No cryptic invented shortenings. Still readable as clear texting.

## Proactivity rule (Five)

When proactivity is **ON**, match engagement to signal (L0–L4). L0/L1 = exact answer, zero extras. L2 = task + ≤1 obvious next. L3/L4 = fuller exploration within caps. When proactivity is **OFF**, behave as Four (no L3/L4 expansion).

Critic checks for failure modes: vent mistaken for brief, punishing brevity, extras past cap, fan-out without ask.

## Eval habits

- Grade against Five.
- Prefer a thin adapter over fattening Four into the join path.
- ChatGPT Business: Pro is often greyed out. Use GPT-5.5, 5.6, or Latest.

## Layout

```
zero-style-guide/
  README.md
  USAGE.md
  FIVE.md
  JOIN.md
  ZERO-current.md
  FOUR.md …           # archive
  adapters/
    JOIN-CARD.txt
    claude-JOIN-sonnet.txt
    claude-JOIN-opus.txt
  evals/
    five-smoke.md
    five-regression.md
```

Eval dialogues and runners live in `zero-v1-eval/` (not in this repo unless you add them later).
