# Usage

How to run Zero without getting lost.

**Package:** `2026-09-08`  
**Canon:** Four (`FOUR.md`, ~5.2k tokens)  
**Join card:** `JOIN.md` (~770 tokens after harden)  
**Feel:** warm, simple, direct builder peer  
**North star:** make the user more productive

## Pick the right file

| Need | Use |
|------|-----|
| Agent just joined a chat | Paste all of `JOIN.md` |
| Grade a dialogue | `FOUR.md` |
| Change the personality rules | `FOUR.md`, then refresh Join |
| Model still fails on Join alone | Thin file under `adapters/` |
| Mirror of current canon | `ZERO-current.md` |

Join is the absorb path. Four is the source of truth. Critic always grades against Four, never Join alone.

## Agent join (30 seconds)

1. Open `JOIN.md`.
2. Paste it as the first system or user context when the agent joins.
3. Keep design and grading on `FOUR.md`.

That’s it. Don’t dump Four into the join.

## Versioning

Edition names: `Zero` → `One` → `Two` → `Three` → **`Four`**.

- New **edition** when canon rules move enough for a new Critic baseline.
- New **package date** when Join, adapters, or this doc change and Four stays put.
- Join can lag Four while you harden. Ship Join only when it all-passes against Four.

### Pins right now (`2026-09-08`)

| Artifact | Pin |
|----------|-----|
| Canon | Four @ `FOUR.md` |
| Join | Hardened Join card (roleplay-only, invite golds, LEN/PX locks) |
| Adapters | `adapters/claude-JOIN-sonnet.txt`, `adapters/claude-JOIN-opus.txt` (Sonnet A6 needs a user-prompt casing lock in the smoke runner) |
| Eval packs | G1–G8 + ADV A1–A8 + B1–B8 under Four |
| Join smoke (known pass) | Grok 24/24, Claude Haiku/Sonnet/Opus 24/24 (+ thin adapters where needed), ChatGPT 5.5 24/24 (JOIN-FULL) |

## Invite rule (Four)

Ask means yes for adding a human or agent to an event, place, channel, or plan room. Do it and report.

Confirm only when access is lasting or destructive (ACL, permanent write, irreversible deletes).

## Eval habits

- Grade against Four.
- Prefer a thin adapter over fattening Four into the join path.
- ChatGPT Business: Pro is often greyed out. Use GPT-5.5, 5.6, or Latest.

## Layout

```
zero-style-guide/
  README.md
  USAGE.md
  FOUR.md
  JOIN.md
  ZERO-current.md
  THREE.md …          # archive
  adapters/
    JOIN-CARD.txt
    claude-JOIN-sonnet.txt
    claude-JOIN-opus.txt
```

Eval dialogues and runners live in `zero-v1-eval/` (not in this repo unless you add them later).
