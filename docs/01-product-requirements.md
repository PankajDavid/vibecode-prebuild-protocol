# Document 1 of 6 — Product Requirements

> **What is being built, for whom, and why — before anything is designed or coded.**

| | |
|---|---|
| **Product** | [Product name] |
| **Prepared by** | [Your name] |
| **Date** | [Date] |
| **Status** | Draft — pending approval |

**How this fits:** fill the documents in order: 1 Product Requirements → 2 Technical Architecture → 3 Security & Access → 4 Frontend Specification → 5 Feature Tickets. Approve 1–4 before generating 5. No code until the ticket list exists. Document 6 (Security Audit) is used after building.

**Vibe-coder tip:** if you don't know an answer, write `Unknown`. An honest gap is better than a confident guess, because the AI will treat whatever you write as true.

---

## 1. Problem statement

### The problem
State the problem in plain language, from the user's point of view — not your solution. If you can't describe it without mentioning your product, you haven't found the problem yet.

[Write here]

### Who has this problem
- Primary user group, and roughly how many of them (be specific — not "everyone"):
- Where they go to solve it today (a competitor, a spreadsheet, WhatsApp, nothing):
- How painful it really is (a mild annoyance and a business-breaking problem need very different products):

### Why now
What changed that makes this worth building now, and why you're the right person to build it.

[Write here]

---

## 2. Target users

| Persona | What they're trying to do | Where today's option fails them |
|---|---|---|
| [Persona 1] | [Goal] | [Frustration] |
| [Persona 2] | [Goal] | [Frustration] |

---

## 3. Goals and non-goals

### Goals for this build
Write outcomes, not features. "Workers understand an English notice in under a minute", not "add a translate button".
- [Goal 1]
- [Goal 2]
- [Goal 3]

### Non-goals (deliberately out of scope)
- [Something this build will NOT do]
- [Something deferred to later]

> Non-goals matter as much as goals. AI coding tools will happily build things you never asked for unless you tell them, in writing, what to leave out.

---

## 4. Core features — first version only

| Feature | User story | Priority |
|---|---|---|
| [Feature] | As a [user], I want to [action] so that [outcome]. | Must |
| [Feature] | As a [user], I want to [action] so that [outcome]. | Should |
| [Feature] | As a [user], I want to [action] so that [outcome]. | Could |

**Must** = the product is useless without it. **Should** = important but can wait a week. **Could** = nice to have.

---

## 5. How you'll know it worked
- Main measure (with a number and a timeframe): [e.g. 20 restaurants using it daily within 60 days]
- Second measure:
- Early signal you can check before the main measure is possible:

---

## 6. Assumptions and constraints

**Assumptions** — things you believe but haven't proven:
- [Assumption]

**Constraints** — budget, deadline, team size, rules, platform limits:
- [Constraint]

---

## 7. Open questions

| # | Question | Who answers it | Status |
|---|---|---|---|
| 1 | [Something unresolved that could change the scope] | [Name] | Open |

---

## 8. Approval

Once approved, this document is locked. Later changes are **scope changes**: write them down here, don't let them slip in silently.

| Role | Name | Date | Approved |
|---|---|---|---|
| Product owner | | | ☐ |
| Technical reviewer | | | ☐ |

**Building solo?** You hold both roles. Re-read it the next day before you approve it. You'll catch things you missed.
