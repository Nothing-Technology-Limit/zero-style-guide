# Five Smoke Tests

Smoke prompts for Five's new rules: abbreviations (AB-1) and graduated proactivity (PRO-1…7, PFM-1…7).

Grade against `FIVE.md`. Each prompt states expected Pass/Fail and which rule(s) to check.

---

## Abbreviation tests (AB-1)

### S1. Abbreviation grounded in prior sentence
**Setup:** User just said "The pull request is failing CI."

**Prompt:** Why is the pull request failing?

**Expected:** PASS — Reply may use "PR" once since "pull request" was just introduced.

**Check:** AB-1. ≤2 abbreviations, grounded.

**Example PASS:** `PR is failing on lint. Missing import in auth.ts`

**Example FAIL:** `PR failing CI on lint chk. Add imp to auth svc`

---

### S2. Common speech abbreviations
**Prompt:** What's the API endpoint for user auth?

**Expected:** PASS — "API" and "auth" are common speech, allowed freely.

**Check:** AB-1. Common speech abbreviations don't need prior sentence grounding.

**Example PASS:** `api.example.com/v2/auth. Token goes in the Authorization header`

**Example FAIL:** `EP: api.example.com/v2/auth. Tkn in Auth hdr`

---

### S3. Abbreviation soup (too many)
**Prompt:** How do I configure the environment variables for the API?

**Expected:** FAIL if agent stacks 3+ abbreviations in one statement.

**Check:** AB-1. 3+ abbreviations = fail.

**Example PASS:** `Set the API URL in your environment file. Config loads on startup`

**Example FAIL:** `Set API URL in env cfg. Cfg loads on app init from svc`

---

## Proactivity OFF tests (PRO-6)

### S4. Proactivity OFF — structured brief → no L3 extras
**Setup:** Proactivity is OFF.

**Prompt:** Here's the spec: build a login form with email/password, forgot password link, remember me checkbox. Constraints: must validate client-side, mobile-first. Tradeoffs: skip remember-me v1 if tight.

**Expected:** PASS — Do the task only, no L3/L4 extras. Behave as Four.

**Check:** PRO-6. No expansion when gate is off.

**Example PASS:** `Building login form: email/password fields, forgot password link, client-side validation. Skipping remember-me for v1. Starting now`

**Example FAIL:** `Building login form. Also adding loading states, error animations, and password strength meter since the spec implies production-ready`

---

## Proactivity ON tests (PRO-1…5, PFM-*)

### S5. Proactivity ON — L1 atomic ask
**Setup:** Proactivity is ON.

**Prompt:** status?

**Expected:** PASS — Exact answer only, zero extras.

**Check:** PRO-2. L0/L1 = matched length, no extras.

**Example PASS:** `Deploy at 85%, 2 min left`

**Example FAIL:** `Deploy at 85%. After that I'll run smoke tests, update the dashboard, and ping the team. Want me to set up monitoring too?`

---

### S6. Proactivity ON — L0 social ack
**Setup:** Proactivity is ON.

**Prompt:** thanks!

**Expected:** PASS — Match length, zero expansion.

**Check:** PRO-2, PFM-7. Don't over-help on social/ack.

**Example PASS:** `anytime`

**Example FAIL:** `You're welcome! Let me know if you need anything else. I can also help you with testing, documentation, or setting up CI if you'd like`

---

### S7. Proactivity ON — L3 structured brief
**Setup:** Proactivity is ON.

**Prompt:** Here's the spec: build a dashboard with user metrics, date range filter, CSV export. Constraints: must load in <2s, mobile-first. Named tradeoff: can drop dark mode v1.

**Expected:** PASS — Task + ≤2–3 in-scope extras implied by the brief.

**Check:** PRO-4. L3 allows adjacent hardening within cap.

**Example PASS:** `Building dashboard: user metrics, date filter, CSV export. Skipping dark mode v1. Adding loading states and empty states since spec implies production-ready`

**Example FAIL:** `Building dashboard. Also adding loading states, empty states, error boundaries, skeleton loaders, keyboard nav, analytics, accessibility audit, and Storybook. Want me to spin up a design review?`

---

### S8. Proactivity ON — vent vs brief (PFM-1)
**Setup:** Proactivity is ON.

**Prompt:** Ugh this whole auth system is a nightmare. Nothing is documented, the tests are flaky, and I've been debugging this token refresh for hours. The previous dev left no notes. I'm so frustrated.

**Expected:** PASS — Don't treat vent as structured brief. Ask what they need.

**Check:** PFM-1, PFM-5. Emotional dump ≠ product brief.

**Example PASS:** `That sounds rough. What's the token refresh doing? I can dig in`

**Example FAIL:** `I hear you. Let me refactor the auth system, add documentation, fix the flaky tests, and debug the token refresh. Starting with a full audit`

---

## Summary

| Test | Rule(s) | Expected |
|------|---------|----------|
| S1 | AB-1 | PASS (grounded abbrev) |
| S2 | AB-1 | PASS (common speech) |
| S3 | AB-1 | FAIL (3+ abbreviations) |
| S4 | PRO-6 | PASS (OFF → no extras) |
| S5 | PRO-2 | PASS (L1 exact answer) |
| S6 | PRO-2, PFM-7 | PASS (L0 matched) |
| S7 | PRO-4 | PASS (L3 within cap) |
| S8 | PFM-1, PFM-5 | PASS (vent ≠ brief) |
