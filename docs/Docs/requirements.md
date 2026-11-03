# PRD: Runway (working title)
**AI money coach built around how students actually get paid**

| | |
|---|---|
| Owner (PM) | Ellis |
| Status | Draft v0.1 |
| Last updated | 24/10/2026 |
| Target | MVP with real student testers before the targetjobs AI Innovator of the Year deadline (expected ~late 01/2027) |

---

## 1. Problem

Students don't get paid monthly. Most income arrives in **lumps**: a Maintenance Loan instalment at the start of each term, irregular part-time wages, occasional parent top-ups. Every mainstream budgeting tool (Monzo, Emma, Cleo) assumes a monthly salary. So students can't easily answer the questions they actually ask:

- "Will my loan last until the next instalment?"
- "Can I afford this night out without being skint in week 9?"
- "How long until I can afford that trip?"

### Evidence (Save the Student, National Student Money Survey 2025)
- Average student spend: **£1,142/month**; average Maintenance Loan: **£640/month**, so a **£502/month shortfall**
- **76%** worry about making ends meet; **50%** say money worries hurt their mental health; **59%** say it hurts their social life
- **93%** say they budget, yet **71%** wish they'd had better financial education
- **61%** skip meals to save money
- **38%** say they weren't made aware of bursaries/grants; only **13%** have received uni hardship funding
- Benchmarks for "people like you": rent £529, groceries £146, going out £61, takeaways £49, transport £67 per month

**Takeaway:** students already *try* to budget. The tools don't fit their income pattern, and the stress is real.

---

## 2. Target user

**Primary persona: "Term-time Tom"**
- UK undergrad, living away from home, on a Maintenance Loan + part-time job
- Banks with Monzo/Starling/a high-street student account
- Knows roughly what's in the account today; has no idea if it'll last the term
- Will not set up a spreadsheet; will ask a chatbot a question

**Secondary:** students saving for a specific goal (trip, deposit, Kilimanjaro-style fundraiser).

---

## 3. Competitive landscape

| Product | What it does well | Gap Runway fills |
|---|---|---|
| **Cleo** | Conversational AI money coach for young people; relaunched in UK (02/2026) | Not built around **termly loan instalments** or student life events |
| Monzo / Starling | Auto-categorisation, pots, spending insights | Monthly framing; no "runway to next loan" or "can I afford tonight" |
| Emma / Snoop | Multi-bank aggregation | Generic; requires open-banking link |
| Spreadsheets | Fully custom | Manual effort; 93% budget but few stick at it |

**Positioning:** *Cleo for students: the only coach that thinks in terms, not months.*

---

## 4. Solution overview

1. **Import:** upload a bank CSV export (no bank login, no scraping)
2. **Understand:** AI categorises every transaction into student-specific categories and learns from corrections
3. **Model income:** user enters loan instalment dates/amounts, wages, parent support → app builds a **term cash-flow forecast**
4. **Coach:** chat interface answering "how am I doing / can I afford X / how long to save for Y", grounded in the user's real data and benchmarks

### Core principle: the AI interprets, the code calculates
The LLM handles language and judgement (categorising messy merchant names, understanding questions, explaining results). **All money maths is deterministic Python** that the LLM calls as tools. This avoids hallucinated numbers, and it's a strong design story for the award and interviews.

---

## 5. Requirements (MoSCoW)

### Must have (MVP)
| ID | Requirement | Acceptance criteria |
|---|---|---|
| M1 | CSV import for **Monzo** and **Starling** | Parses dates as day-first (dd/mm/yyyy); handles £ amounts, in/out sign; rejects bad files with a clear message |
| M2 | AI categorisation into student categories | Categories: Rent, Groceries, Going out, Takeaways & eating out, Transport, Bills, Course materials, Subscriptions, Shopping, Health, Societies & sport, Income: loan, Income: wages, Income: other, Transfers |
| M3 | Learns from corrections | Correcting a merchant once applies to all past and future transactions from that merchant |
| M4 | Income setup | User enters loan instalment dates + amounts, regular wages, other income |
| M5 | **Runway forecast** | Shows projected balance up to next loan instalment; flags the date money runs out at current spend |
| M6 | **"Can I afford it?"** | Given an amount (e.g. £40 night out), shows impact on runway and a safe-to-spend figure for the week |
| M7 | **Savings goal calculator** | Given goal (£ + optional date), returns time-to-goal at current rate and the weekly cut needed to hit a date |
| M8 | Chat interface | Natural-language questions answered using M5–M7 tools and the user's data; never invents numbers |
| M9 | Privacy baseline | Data stored locally/per-user; no real bank data committed to the repo; one-click delete all data |

### Should have
| ID | Requirement |
|---|---|
| S1 | Generic CSV importer: AI maps unknown bank column layouts (Barclays, Santander, Lloyds, Nationwide…) |
| S2 | Peer benchmarks: "you spend £X on going out vs £61 student average" |
| S3 | Subscription & recurring-charge detection |
| S4 | Weekly summary ("this week vs your plan") |
| S5 | Signposting: if runway goes negative, point to uni hardship funds / Student Union advice (non-judgemental) |

### Could have
| ID | Requirement |
|---|---|
| C1 | Open banking via a regulated provider (later; free GoCardless Bank Account Data tier is closed to new signups) |
| C2 | Shared house bills splitting |
| C3 | Term-calendar awareness (freshers, Christmas, exam season spending spikes) |
| C4 | Mobile-friendly PWA |

### Won't have (this phase)
- Investment, credit or loan recommendations (regulated territory)
- Storing bank login credentials or scraping banks
- Multi-currency

---

## 6. Non-functional requirements
- **Accuracy:** categorisation ≥90% correct on a labelled test set before user testing
- **Speed:** first insight within 2 minutes of upload
- **Cost:** cache categorisations per merchant so the LLM isn't called for every transaction
- **Tone:** supportive, never shaming; plain English; no "financial advice" framing
- **Data protection (UK GDPR):** testers give informed consent; minimal data retained; test data anonymised for any write-up

---

## 7. Success metrics
| Metric | Target by application |
|---|---|
| Active testers (real students, own data) | ≥10 |
| Categorisation accuracy (after corrections) | ≥90% |
| Runway forecast error vs actual at 2 weeks | Track and report |
| Tester confidence about money (1–5, before vs after 2 weeks) | Measurable increase |
| Testers who'd keep using it | ≥60% |

---

## 8. Technical approach (proposed)
- **Language:** Python
- **Data:** SQLite (SQL for queries/aggregations)
- **UI:** Streamlit for MVP (fastest path to something testers can use); revisit later
- **AI:** Claude API. Small/fast model for categorisation; stronger model for chat with tool calling into M5–M7 functions
- **Testing:** pytest; synthetic sample CSVs in `data/samples/` (never real statements)

---

## 9. Risks
| Risk | Mitigation |
|---|---|
| Cleo's UK relaunch makes this look like a copy | Lead with the term/loan cash-flow model and student context, which Cleo doesn't do |
| Bank CSV formats vary and have quirks (e.g. day-first dates; Monzo exports include Pots transfers) | Start with 2 banks; build a format test suite; AI column-mapper as S1 |
| LLM gives wrong numbers | Maths only in code; LLM must call tools; tests on tool outputs |
| Testers unwilling to share bank data | Local-first, CSV-only, delete button, clear consent form |
| Scope creep vs deadline | MoSCoW above is the contract; changes go in `docs/decisions.md` |

---

## 10. Milestones
| Phase | Deadline | Exit criteria |
|---|---|---|
| Discovery | 08/11/2026 | 5–10 student interviews done; PRD v1 updated with findings |
| MVP build (M1–M9) | 13/12/2026 | Ellis using it on his own data |
| Tester round 1 | 03/01/2027 | ≥10 testers onboarded; feedback logged |
| Iterate (v2) | 17/01/2027 | Top 3 issues fixed; metrics collected |
| Award application | ~23/01/2027 | Essays drafted from decision log + metrics (confirm real deadline when published) |

---

## 11. Open questions
- Does the 2027 award have the same sponsor and essay questions? (check when published)
- Which banks do Lancaster students actually use? (ask in interviews)
- Web app vs local app for testers?
- Final product name
