# ConsumerSuit — UK Legal-Tech AI Platform

> **"Stand up for yourself, without the £200-an-hour bill."**

**Live site:** [consumer-suit.uk](https://consumer-suit.uk)  
**Portfolio demo:** [hrushimanju.github.io/ConsumerSuit](https://hrushimanju.github.io/ConsumerSuit) *(update after Pages setup)*  
**Built:** May – June 2026 · **Status: In active development — pre-launch

---

## What it is

ConsumerSuit is a consumer-facing UK legal self-help platform. Users describe a dispute — employment, housing, consumer rights, data protection, travel — and the platform:

1. **Analyses** the dispute against applicable UK law (EqA 2010, ERA 1996, CRA 2015, GDPR, etc.)
2. **Maps** their evidence — STRONG / WEAK / MISSING — against what a claim needs
3. **Builds** a draft claim document, complaint letter, or DSAR

The product covers **28 civil law areas**, verified against [legislation.gov.uk](https://legislation.gov.uk), with compensation figures current to **6 April 2026** (new tribunal caps, Vento bands, Ofcom limits).

Two halves:
- **The app** (`/`) — AI-powered 3-phase flow with subscription tiers (£9 / £29 / £79 / £149)
- **The wedges** (`/flight.html`, `/parking.html`, `/council.html`, `/section75.html`) — focused, zero-AI-cost checkers with lead capture

---

## My role

I am the **founder and product lead**. I did not write the code — that was my AI co-builder. What I did:

| My contribution | Impact |
|---|---|
| **Vision and product definition** — what it is, who it's for, what it costs | Shaped the entire product |
| **QA leadership** — 5-case accuracy harness; found critical gaps; directed fixes | Correct statutory sections, real settlement figures |
| **Security instinct** — caught AI prompts exposed in browser DevTools | Protected the core IP before launch |
| **Technology decisions** — trialled NVIDIA NIM; rejected at 67s; reverted | Kept UX acceptable |
| **Pricing strategy** — pushed from £3–£29 to £9–£149 | Proper commercial signal |
| **Brand and domain** — registered `consumer-suit.uk`; named 360 Three Sixty | Product identity separate from personal identity |
| **Documentation** — `PROJECT_LOG.md` + `FOUNDER_JOURNAL.md` throughout | Decisions recorded with rationale |

---

## Technical stack

```
User → Cloudflare Pages + Edge Functions (consumer-suit.uk)
         ├── D1 SQLite          — users, sessions, subscriptions
         ├── KV store           — leads, feedback, funnel metrics
         ├── Stripe             — checkout, webhooks, customer portal
         ├── Google OAuth       — sign-in, session tokens
         └── AI fallback chain  — Anthropic → Mistral → Groq (Premium)
                                — 1,000/day circuit breaker
                                — Server-side prompts (never client-exposed)
```

**Legal knowledge layer (server-side only):**  
Compressed system prompt (~5.5k tokens) · EqA 2010 section discipline · NMW floor check ·  
Vento bands (2026) · DSAR Art.82 · CCA s.75 · Limitation period warnings · Settlement aggregation

---

## Engineering transferable skills

This project maps directly to engineering competencies:

| Skill | What I did | Engineering equivalent |
|---|---|---|
| **V&V** | 5-case accuracy harness; found statutory section errors and settlement undercount; directed fixes; re-run confirmed improvements | Test design, defect tracking, corrective action |
| **Systems architecture** | Multi-provider fallback chain with rate limiting + circuit breakers | Redundant system design, FMEA, reliability |
| **Risk assessment** | Found IP exposure vulnerability; led remediation before launch | Hazard identification, FMEA, risk closure |
| **Requirements engineering** | Translated complex legal domain into precise technical specs | SRS, functional decomposition, traceability |
| **Performance engineering** | Benchmarked NVIDIA at 67s; quantitative rejection; rationale logged | Load testing, technology evaluation |
| **End-to-end delivery** | 0 → test-deployed product in 16 days | Sprint execution, milestone management |
| **Technical documentation** | PROJECT_LOG + FOUNDER_JOURNAL with decisions and rationale | Design records, lessons-learned, engineering notebooks |

---

## Key decisions (engineering rationale)

**Prompt compression (–16%, 6,500 → 5,500 tokens)**  
Reduced AI cost per call while maintaining a 55-point substance check. Tradeoff: precision over verbosity.

**NVIDIA NIM rejection**  
Trialled as primary provider. Benchmarked at 67 seconds response time against <5s target. Rejected on quantitative grounds. Clean revert with decision logged. Lesson: "more powerful" ≠ better if the UX is unusable.

**Server-side prompts**  
Original build exposed AI prompts client-side (visible in browser DevTools). This is the product's core IP. Moved fully server-side before public launch.

**Pricing: £9 / £29 / £79 / £149 (revised from £3 / £7 / £15 / £29)**  
Original pricing signalled "cheap tool". The target user is someone with a real dispute — a solicitor costs £200/hour. At £29/month you're still cheap by comparison and the price communicates that the output is serious.

---

## Accuracy approach

The legal accuracy framework is the product's core asset:

- **QA scorecard:** 5 cases (employment, housing, broadband, used car, CCA s.75) with scoring across 8 dimensions
- **Defects found:** wrong EqA sections; NMW not checked; settlement not aggregated across all heads; sector regulatory layer missing
- **Fix process:** ranked fix list → prompt update → full re-run → all 4 cases pass
- **Ongoing:** weekly robot cross-checks all 28 law summaries against legislation.gov.uk; rewrites only when source has changed
- **Compensation figures:** updated to 6 April 2026 — tribunal weekly pay cap (£751), compensatory cap (£123,543), Vento bands, Ofcom limits

---

## Regulatory position

Confirmed sound (13 June 2026 board review):
- Outside reserved legal activities under the Legal Services Act 2007
- Not an FCA-regulated claims management company (no taking of fees for claiming)
- AI output carries score/settlement caveats and one-time acknowledgement gate
- Document-draft banner distinguishes tool output from legal advice

---

## Project files

| File | Purpose |
|---|---|
| `PROJECT_LOG.md` | What was built, when, and current status |
| `FOUNDER_JOURNAL.md` | My personal record — decisions, ideas, rationale |
| `demo/index.html` | Standalone portfolio demo (GitHub Pages) |

---

## Author

**Hrushikesh Manjunath Thotamsetty**  
AMIMechE #80821391 · CEng pathway · MSc Mechanical Engineering, University of Liverpool  
manjunathhrushikesh@gmail.com · [consumer-suit.uk](https://consumer-suit.uk)

---

*This repository is a portfolio case study. The production codebase is deployed via Cloudflare Pages from a private repository.*
