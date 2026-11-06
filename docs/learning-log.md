# Learning log

What I've learned building Runway, in my own words. One entry per session.

Format:
- **Date** (dd/mm/yyyy)
- **What I worked on**
- **New concepts**: term, plain-English meaning
- **What confused me / still unsure about**
- **How I'd explain it to someone else**

---

## 24/10/2026: Project kick-off
**Worked on:** researching the AI Innovator of the Year award, the student money problem and competitors; writing the PRD.

**New concepts**
- **PRD (Product Requirements Document):** the agreed description of what to build, for whom, and how success is measured. The team builds from it.
- **MoSCoW:** a way to prioritise. **M**ust have, **S**hould have, **C**ould have, **W**on't have (for now).
- **Acceptance criteria:** the specific tests that decide whether a requirement is "done".
- **API key:** a password that lets my app send requests to an AI model; usage is paid per token.
- **Token:** a chunk of text (roughly ¾ of a word) that AI usage is measured and charged by.
- **Open banking:** regulated way for apps to read bank data with the user's permission; needs a licensed provider, so the MVP uses CSV exports instead.

**Still unsure about:**

**How I'd explain it:**

---

## 06/11/2026: Moving docs into place and pushing to GitHub
**Worked on:** moving the docs out of a wrongly-nested `docs/Docs/` folder into `docs/` so the README's links work, updating the decision log, adding `ideas.md` and `survey.md`, and fixing a GitHub login mismatch that blocked pushing.

**New concepts**
- **git clone:** makes a full copy of a remote repository (e.g. one on GitHub) onto your own computer, including its entire history. The usual first step before working on a project locally.
- **git pull:** downloads the latest commits from GitHub and merges them into your local copy, so you're working from the latest version before you start changing anything.
- **git mv:** the git-aware way to move or rename a file. It stages the old path as removed and the new path as added in one step, so git recognises it as a *rename* and keeps the file's history attached, instead of seeing an unrelated delete-and-add.
- **git diff (--staged):** shows the exact line-by-line changes about to be saved — what's added, removed or moved — so you can check them before committing.
- **git commit:** saves everything staged as a permanent snapshot in the project's history, with a message explaining what changed and why.
- **git push:** uploads your local commits to GitHub, so they're backed up there and visible to anyone looking at the repo.

**Still unsure about:**

**How I'd explain it:**
