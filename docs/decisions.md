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

**05/11/2026 | Privacy concern raised; kill criterion set**
- Trigger: an early informal conversation: a student said she wouldn't want an AI to see her bank statements. Matches assumptions A2 and A5.
- Decision: make privacy a headline feature (runs locally; only merchant names sent to the AI; chat sees totals only; "see what the AI sees" preview; delete-all button). Let survey Q12 decide whether the concept survives: ≥60% Yes/Maybe → continue; 40–60% → continue and test the privacy design; <40% → rethink.
- Alternatives: drop the idea on one reaction (too little evidence); ignore it (risks building something nobody will use).

**05/11/2026 | Stay with the finance tracker; park the driving-instructor idea**
- Why: scored both ideas against the project goals. Finance tracker: AI is core, I personally have the problem, and I can reach 10 student users by January. Driving-instructor booking system: crowded market (Total Drive, MyDriveTime, Bitepoint and others), AI would be bolted on, and it needs real businesses and learners on both sides, which is too slow for the award timeline.
- Alternatives: switch to the driving idea (parked in ideas.md as a possible future business).
