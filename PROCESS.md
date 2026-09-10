# How we made Zero (process)

Short version of how Four + Join got built. Written in Zero voice on purpose.

**Repo:** https://github.com/Nothing-Technology-Limit/zero-style-guide
**Canon:** `FOUR.md`
**Join card:** `JOIN.md`
**When:** 2026-09-05 to 2026-09-09

## What we were building

Zero is a phone-chat builder peer. Warm, simple, direct. Makes the user more productive. Must not sound like a model or a support bot.

The guide had to be testable. Vague vibes die. Rules need Pass / Fail lines a Critic can grade.

## The loop

We used a small agent loop, not a one-shot draft.

1. **Persona Designer** owns the living guide (voice, rules, exemplars).
2. **Eval Runner** runs fixed packs on real models (Grok, Claude, ChatGPT).
3. **Style Critic** grades outputs against current canon only.
4. **Chief of Staff** orchestrates, ships docs, pushes GitHub.

Pattern every edition:

1. Change the guide (or add an exemplar).
2. Smoke the pack.
3. Critic scores.
4. Harden the rule or add a thin adapter.
5. Re-smoke until all-pass.
6. Lock the edition name. Move on.

No big redesign mid-flight. Fix what failed.

## Edition path

Names are words: Zero, One, Two, Three, then **Four**.

| Edition | What landed |
|---------|-------------|
| Zero | First concrete guide from James brief |
| One | Ban AI-slop punctuation. Middle register (clear texting, not essay, not smash) |
| Two | Soft prefs assumed. One blocking ask max |
| Three | Long how-tos: max 5 steps or short TLDR. Ask host/repo/env before dumping steps |
| Four | Invite/seat: do and report. Confirm only lasting ACL / destructive. Later: failure behavior (FB-1 to FB-7) for live tools |

Archive old editions in the repo. Keep one canon file: `FOUR.md`.

## Join card (why it exists)

Four is about 5k tokens. Too heavy to paste when an agent joins a chat.

So we shipped `JOIN.md`: lean absorb card (about 770 tokens). Same persona. Critic still grades against **Four**, never Join alone.

Rule: Join can lag while you harden. Ship Join only when it all-passes vs Four.

## Eval packs

Three packs, Critic-graded vs Four:

- **G1 to G8** - gold happy path
- **A1 to A8** - adversarial / escape
- **B1 to B8** - harder adversarial (format jailbreaks, long dumps, ID traps)

Known Join all-pass (24/24): Grok, Claude Haiku / Sonnet / Opus (thin adapters where needed), ChatGPT 5.5 / 5.6 / Latest. ChatGPT 5.6 needed Custom Instructions for a couple of hard IDs. Pro / GPT-6 was unavailable in the picker.

## What actually worked

- Testable rules beat taste essays.
- Exemplars (gold + fail) teach faster than paragraphs.
- Thin per-model adapters beat fattening Four for one model quirk.
- Split packs (G then A then B) for ChatGPT browser runs. Long one-shots lied.
- Invite policy in plain English: ask means do it. Confirm only when access is lasting or destructive.
- Failure behavior for live tools: what failed + one next step. Never fake success. Prove in beta. Skip more model smokes for that add.

## What to steal if you copy this

1. Write the persona as Pass / Fail rules.
2. Keep a short Join card separate from full canon.
3. Run the same packs across models. Grade against one canon.
4. Harden from fails, not from vibes.
5. Publish the package. USAGE.md tells people which file to open.

## Files to open

| File | Why |
|------|-----|
| `USAGE.md` | 30-second start |
| `FOUR.md` | Full canon + grading |
| `JOIN.md` | Paste when an agent joins |
| `adapters/` | Thin locks for stubborn models |

That's the process. Ship, measure, harden, rename the edition when the baseline moves.
