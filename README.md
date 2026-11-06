# AI Student Finance Tracker

**An AI money coach for UK students, built around how students actually get paid.** Import your bank statement, get spending categorised automatically, and ask things like *"can I afford a night out this week?"* or *"how long until I can afford this trip?"*

**Status:** 🟡 Discovery: requirements drafted, student interviews in progress. No code yet.

---

## Why I'm building this
I built a [Google Sheets budget tracker](https://github.com/ellisoutterside/sheets-budget-tracker) for myself at uni. It worked, but it was rigid: keyword rules miscategorised things, it couldn't learn from corrections, and it only answered "what did I spend?", not "what should I do?". This is the proper version, designed for students in general rather than just me.

## The problem
Students don't get paid monthly. Most of their money arrives in lumps: a Maintenance Loan instalment each term, irregular part-time wages, occasional help from family. Mainstream budgeting apps assume a monthly salary, so they struggle with the questions students actually ask:

- *"Will my loan last until the next instalment?"*
- *"Can I afford this night out without being skint in week 9?"*
- *"How long until I can afford that trip?"*

According to Save the Student's National Student Money Survey 2025, the average student faces a **£502/month shortfall** between their Maintenance Loan and living costs, and **76%** worry about making ends meet. **93%** already try to budget; the tools just don't fit how they're paid.

## Planned features (MVP)
- Import bank statements via CSV (no bank logins, no scraping)
- AI categorisation into student-relevant categories that improves when corrected
- **Term forecast:** how long your money will last until the next loan instalment
- "Can I afford it?" checks and savings-goal planning
- Ask questions in plain English, answered from your real figures

**Design principle: AI interprets, code calculates.** The AI handles language and judgement. Every money calculation is plain, tested Python, so the app never gives a made-up number.

## How I'm running it
I'm treating this as a product, not just a coding project. I'm acting as product owner and business analyst, and directing an AI-assisted build with Claude Code:

1. **Discover:** interview students about how they manage money and where it goes wrong
2. **Define:** turn findings into requirements and user stories with acceptance criteria
3. **Plan:** prioritise a backlog and plan delivery in small milestones
4. **Build:** use Claude Code to implement one user story at a time
5. **Check:** test each feature against its acceptance criteria before moving on
6. **Document:** record decisions, risks and lessons as I go

## Roadmap
- [x] Draft requirements and user stories
- [x] Draft user interview questions
- [x] Prioritise the backlog (MoSCoW)
- [x] Choose a provisional tech stack
- [ ] Interview students and update requirements
- [ ] Build the MVP
- [ ] Test with 10+ students
- [ ] Iterate on feedback

## Docs
| Document | What it shows |
|---|---|
| [Requirements](docs/requirements.md) | Problem, evidence, users, competitors, priorities, success metrics |
| [User stories](docs/user-stories.md) | Requirements from the user's view, with acceptance criteria |
| [Interview questions](docs/interview-questions.md) | User research script |
| [Decision log](docs/decisions.md) | Key decisions, reasons and alternatives considered |
| [RAID log](docs/raid-log.md) | Risks, assumptions, issues and dependencies |
| [Stakeholders](docs/stakeholders.md) | Who's affected and how they're involved |
| [Learning log](docs/learning-log.md) | What I've learned along the way |
| [Ideas parking lot](docs/ideas.md) | Ideas parked for later, and why |
| [Discovery survey](docs/survey.md) | Survey questions and analysis plan |

## Tech (provisional)
Python · SQLite · Streamlit · Claude API · pytest

## Privacy
No bank logins are stored and no banks are scraped. Real statements never go in this repository; only synthetic sample data is used for testing.
