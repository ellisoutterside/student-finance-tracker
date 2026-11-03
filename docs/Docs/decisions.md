# Decision log

Format: **Date | Decision | Why | Alternatives considered**

---

**24/10/2026 | Target UK students specifically, framed around termly loan instalments**
- Why: generic AI budgeting already exists (Cleo relaunched in UK 02/2026). Students' lump-sum income is the unmet need. NSMS 2025: £502/month average shortfall, 76% worry about money.
- Alternatives: general personal finance app (crowded); personal-only tool (no award/CV story).

**24/10/2026 | CSV import, not bank scraping or open banking, for MVP**
- Why: scraping breaks bank terms and security; open banking needs a regulated provider (GoCardless's free Bank Account Data tier is closed to new signups). CSV exports exist in Monzo/Starling/most banks and keep users in control of their data, which helps tester trust.
- Alternatives: open banking aggregator (revisit as C1 once there are users).

**24/10/2026 | AI interprets, code calculates**
- Why: LLMs can produce wrong numbers. Deterministic Python for all money maths; the chat model calls these as tools. Easier to test, safer, better story.
- Alternatives: let the LLM reason over raw transactions (cheaper to build, unreliable).

**24/10/2026 | Start with Monzo + Starling importers**
- Why: popular with students, clean CSV exports. Generic AI column-mapper later (S1). To validate in interviews.

**03/11/2026 | Discovery deadline moved from 08/11 to 15/11**
- Why: repo setup took longer than planned alongside uni work; interviews hadn't started.
- Impact: MVP build starts a week later; December target kept by tightening build scope if needed.
