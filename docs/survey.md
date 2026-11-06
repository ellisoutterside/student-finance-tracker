# Discovery survey (Google Forms)

> **What this is:** a short online survey to get numbers alongside the interviews.
> **Interviews = depth (why). Survey = breadth (how many).**
> **Target:** 30–50 responses by 15/11/2026. Takes ~3 minutes.
> **Rules:** no names, no emails, no bank details, no exact balances. Every question optional except Q1.

---

## Intro text (top of the form)
> I'm a Lancaster CS student researching how UK students manage money at uni, for a project building a better budgeting tool. The survey takes about 3 minutes and is completely anonymous: I won't collect your name, email or any bank details. Results will only be shared as totals. Thanks for helping!

---

## Section 1: About you
| # | Question | Type | Options | Tests |
|---|---|---|---|---|
| Q1 | Are you currently a UK university student? | Multiple choice (required) | Yes / No → *No ends the survey* | Screening |
| Q2 | What year are you in? | Multiple choice | 1st / 2nd / 3rd / 4th+ / Postgrad | — |
| Q3 | Where do you live during term? | Multiple choice | Halls / Shared house or flat / With family / Other | — |
| Q4 | Where does your money come from? | Checkboxes | Maintenance Loan / Part-time job / Family / Savings / Overdraft / Bursary or grant / Other | A1 |

## Section 2: Tracking money
| # | Question | Type | Options | Tests |
|---|---|---|---|---|
| Q5 | How do you keep track of your money? | Checkboxes | Banking app only / Banking app budgeting features (pots, spaces) / Spreadsheet / Notes app / Another budgeting app / I don't really track it | A1 |
| Q6 | Which bank do you mainly use? | Multiple choice | Monzo / Starling / Santander / Barclays / Lloyds / HSBC / NatWest / Nationwide / Other | A3 |
| Q7 | When your loan comes in, how confident are you that it'll last until the next one? | Linear scale 1–5 | 1 = not at all, 5 = very confident | A1 |
| Q8 | In the last term, did you run out of money (or nearly) before your next loan payment? | Multiple choice | Yes / Nearly / No / I don't get a loan | A1 |

## Section 3: Spending decisions
| # | Question | Type | Options | Tests |
|---|---|---|---|---|
| Q9 | How often do you think "can I actually afford this?" before spending on something social? | Multiple choice | Most times / Sometimes / Rarely / Never | A4 |
| Q10 | In the last month, have you skipped a social event because of money? | Multiple choice | Yes, more than once / Once / No | A4 |
| Q11 | Are you saving for anything specific right now? | Short answer | e.g. trip, gig, deposit | US5 |

## Section 4: Tools and trust
| # | Question | Type | Options | Tests |
|---|---|---|---|---|
| Q12 | Would you upload a statement file (CSV) exported from your banking app to a budgeting tool? | Multiple choice | Yes / Maybe, depends on privacy / No | A2 |
| Q13 | How much would you trust an AI to give you advice about your spending? | Linear scale 1–5 | 1 = not at all, 5 = completely | A5 |
| Q14 | What's the most annoying thing about managing money at uni? | Paragraph | — | Open |

## End of form
> Thanks! If you'd be up for testing the tool later this term, message me directly. (Don't add an email field here: keeping contacts separate keeps the survey anonymous.)

---

## Analysis plan (after it closes)
| What | How |
|---|---|
| Totals for each question | Google Forms "Responses" tab → summary charts |
| Key cross-checks | e.g. confidence (Q7) vs ran out (Q8); bank (Q6) for importer priority |
| Write-up | `docs/research/survey-results.md`: top 5 numbers + what they mean for requirements |
| Update | Mark A1–A5 in `raid-log.md` |

**Do the analysis yourself in Google Sheets** (link the form to a sheet, use COUNTIF and pivot tables). Spreadsheet skill is expected in BA and delivery roles.
