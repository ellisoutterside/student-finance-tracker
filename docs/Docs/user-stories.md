# User stories

> **What this is:** requirements written from the user's point of view.
> **Format:** *As a [type of user], I want [goal] so that [reason].*
> Each story has **acceptance criteria**: tests written as *Given [situation], when [action], then [result]* (called "Gherkin" format).
> **Why it matters:** this is the core BA skill. It keeps the team focused on the user's real need, not just features. Each story links to a PRD requirement ID.
>
> **Status:** draft. Rewrite after Discovery interviews.

---

### US1: Import my statement (M1)
**As a** student, **I want** to upload my bank's CSV export **so that** I can see my spending without connecting my bank login.
- **Given** a valid Monzo CSV, **when** I upload it, **then** all transactions appear with correct dates and amounts.
- **Given** a file that isn't a supported CSV, **when** I upload it, **then** I see a clear message explaining what went wrong.

### US2: See where my money goes (M2, M3)
**As a** student, **I want** my transactions sorted into categories automatically **so that** I don't have to label them myself.
- **Given** an imported statement, **when** categorisation runs, **then** each transaction has a student-relevant category.
- **Given** I correct "SPOONS LANCASTER" to *Going out*, **when** I next import, **then** all transactions from that merchant are *Going out*.

### US3: Will my money last? (M4, M5)
**As a** student on a Maintenance Loan, **I want** to know if my money will last until my next instalment **so that** I don't run out before it arrives.
- **Given** my balance, loan dates and spending pattern, **when** I open the dashboard, **then** I see my projected balance up to the next instalment.
- **Given** I'm on track to run out early, **when** I view the forecast, **then** I see the date it runs out and how much less per week would fix it.

### US4: Can I afford this? (M6)
**As a** student, **I want** to ask if I can afford a specific spend (e.g. £40 night out) **so that** I can enjoy myself without guilt or risk.
- **Given** my forecast, **when** I ask about a £40 spend, **then** I see the impact on my runway and a yes / tight / no answer with the reason.

### US5: Saving for something (M7)
**As a** student, **I want** to know how long it'll take to save for a trip **so that** I can plan realistically.
- **Given** a £600 goal, **when** I enter it, **then** I see the time to reach it at my current rate.
- **Given** a target date, **when** I add it, **then** I see the weekly saving needed and where I could cut.

### US6: Just ask (M8)
**As a** student, **I want** to ask questions in normal language **so that** I don't have to dig through charts.
- **Given** a question like "how am I doing this month?", **when** I ask it, **then** the answer uses my real figures and never invented numbers.
