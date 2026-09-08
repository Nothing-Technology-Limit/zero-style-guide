# Zero personality style guide — usage

**Package version:** `2026-09-07`  
**Canon edition:** **Four** (`FOUR.md`, ~5.2k tokens)  
**Join card:** `JOIN.md` / `adapters/JOIN-CARD.txt` (~640 tokens)  
**Persona:** Zero — warm, simple, direct phone-chat builder peer  
**North star:** make the user more productive

## What goes where

| File | Role | When to use |
|------|------|-------------|
| `FOUR.md` | Full canon | Style Critic grading, design edits, long-form reference |
| `JOIN.md` | Lean join payload | Paste into an agent when they join a chat |
| `ZERO-current.md` | Mirror of current canon | Same as Four; convenience symlink/copy |
| `USAGE.md` | This doc | Humans shipping Zero into agents / evals |

Do **not** paste Four into join chats — it’s too heavy for rapid absorb. Join card only; Critic grades against Four.

## Quick start (agent join)

1. Open `JOIN.md`.
2. Paste the whole card as the first system/user context when the agent joins.
3. Keep grading / design work on `FOUR.md` (edition Four).

## Versioning

Edition names: `Zero` → `One` → `Two` → `Three` → **`Four`** (current).

- Bump the **edition** only when canon rules change enough that Critic packs need a new baseline.
- Bump the **package date** (`Package version` above) when Join card, adapters, or this usage doc change without a new edition.
- Join card and Four can diverge briefly during hardening; Join must still grade all-pass against Four before shipping.

### Current pins (2026-09-07)

| Artifact | Pin |
|----------|-----|
| Canon | Four @ `FOUR.md` |
| Join card | ~725 tok hardened (Sonnet fail patch: ID/LEN/PX) |
| Eval packs | G1–G8 + ADV A1–A8 + B1–B8 under Four |
| Join smoke (known pass) | Grok 24/24, Claude Haiku 24/24 |

## Invite policy (Four)

Ask = consent for human/agent adds to events, places, channels, plan rooms. Confirm only lasting ACL / destructive / permanent access.

## Eval notes

- Critic grades dialogues against **Four**, never against Join alone.
- Thin per-model adapters are OK when Join-only fails; don’t fatten Four into the join path.
- ChatGPT Business: Pro may be `aria-disabled` in the picker; GPT-5.5 / 5.6 / Latest are the working lanes.

## Layout

```
zero-style-guide/
  FOUR.md          # canon
  JOIN.md          # join card
  USAGE.md         # this file
  ZERO-current.md  # mirror of canon
  THREE.md …       # prior editions (archive)
```

Eval dialogues and runners live separately under `zero-v1-eval/` (optional to publish).
