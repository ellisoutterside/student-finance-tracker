# CLAUDE.md

## Project
**Runway (working title)**: an AI money coach for UK university students. Users upload a bank CSV; the app categorises spending with AI, models term-based income (Maintenance Loan instalments, wages), forecasts how long money will last, and answers questions like "can I afford a £40 night out?" or "how long to save £800 for a trip?".

Source of truth for scope: `docs/requirements.md`. Decision history: `docs/decisions.md`.

## Roles
- **Ellis = product manager.** He sets requirements and priorities. Keep code simple and readable over clever.
- **Claude Code = engineering team AND teacher.** Build what the PRD says. If a request conflicts with the PRD or seems like scope creep, say so before building.

## Teaching mode (always on)
This is Ellis's first real project and a learning process. Assume he knows very little about tools, Git, Python libraries, APIs or project structure.
1. **Before doing something, say what you're about to do and why**, in one or two plain-English sentences.
2. **Define every new term the first time it appears** (e.g. "a virtual environment is…", "a commit is…"). Use an everyday analogy where it helps.
3. **After writing code, walk through it**: what each file/function does, how the pieces connect, and what would break if it were removed.
4. **Show the commands, don't just run them silently.** Explain what each command does so Ellis could run it himself next time.
5. **Let Ellis do small things himself** when they're simple (e.g. running the app, making a commit), with step-by-step instructions.
6. **End each session with a "What you learned" section**: 3–5 key concepts in plain English, and append them to `docs/learning-log.md` with the date.
7. When there's a choice, **explain the options and trade-offs** and let Ellis decide as PM. Recommend one.
8. If Ellis seems confused, slow down and re-explain differently. Never assume knowledge from a previous session; recap briefly.

## Working rules
1. Before starting a feature, name the PRD requirement ID it implements (e.g. M5).
2. Work in small steps; each step should leave the app runnable.
3. Write pytest tests for every money calculation (runway, affordability, savings goals).
4. **The LLM never does arithmetic.** All money maths lives in plain Python functions; the chat model calls them as tools.
5. Cache AI categorisations per merchant; don't call the API per transaction if the merchant is already known.
6. When a meaningful decision is made (tech choice, scope change, trade-off), append it to `docs/decisions.md` with date (dd/mm/yyyy), decision, reason, alternatives considered.
7. After each session, summarise: what was built, what's next, any open questions for Ellis.

## Data & privacy
- **Never commit real bank statements.** Real data lives in `data/private/` (gitignored).
- Use synthetic CSVs in `data/samples/` for tests and demos.
- API keys only via `.env` (gitignored). Never hardcode.
- No storing bank logins, no scraping banks.

## Conventions
- UK formats: dates dd/mm/yyyy (bank CSVs are day-first), currency £, store amounts as integer pence.
- Python, SQLite, Streamlit (MVP), Claude API.
- Tone of user-facing text: supportive, plain English, never shaming, never framed as regulated financial advice.

## Structure (target)
```
docs/        requirements.md, decisions.md, research/
app/         Streamlit UI
core/        importers/, categoriser.py, forecast.py, goals.py, chat.py
data/        samples/ (committed), private/ (gitignored)
tests/
```
