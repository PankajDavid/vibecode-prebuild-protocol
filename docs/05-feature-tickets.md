# Document 5 of 6 — Feature Tickets

> **The buildable breakdown. This is what you actually give the AI coding tool, one ticket at a time.**

| | |
|---|---|
| **Product** | [Product name] |
| **Prepared by** | [Your name] |
| **Date** | [Date] |
| **Status** | Draft — pending approval |

The most common reason AI-built code breaks is asking for too much in one prompt. **One ticket = one piece of work you can check before moving on.** Generate this list only after Documents 1–4 are approved.

---

## 1. Ticket format

| Field | What goes in it |
|---|---|
| **ID** | Short and stable, e.g. `AUTH-01` |
| **Title** | One line, starting with a verb |
| **User story** | As a [user], I want to [action] so that [outcome] |
| **Acceptance criteria** | Specific things you can test. Not "works correctly". |
| **Depends on** | Tickets that must be finished first |
| **Security notes** | Which Absolute Rules from Document 3 apply |
| **Priority** | Must / Should / Could |
| **Status** | Not started / In progress / Review / Done |

---

## 2. Example tickets

### AUTH-01 — Email and password sign-up with secure storage
- **User story:** As a new user, I want to create an account with email and password so that I can log back in later.
- **Acceptance criteria:** passwords under 8 characters are rejected; passwords are hashed with bcrypt (12 rounds) before storage; a duplicate email gets a generic error (no hint that the account exists); a successful sign-up returns a short-lived login token and a refresh token.
- **Depends on:** nothing.
- **Security notes:** Absolute Rules 5 and 6.
- **Priority:** Must

### AI-01 — Explain an uploaded document in plain language
- **User story:** As a user, I want to upload a photo of a letter and get a simple explanation so that I know what it asks me to do.
- **Acceptance criteria:** only JPG, PNG or WebP under 4 MB accepted (checked on the server); the AI is called only from the server; the answer is shown as plain text, not HTML; more than 10 requests per user per hour are refused with a friendly message; if the AI fails, the user sees a retry message, not a blank screen.
- **Depends on:** the base page layout ticket.
- **Security notes:** Absolute Rules 6, 10 and 11.
- **Priority:** Must

---

## 3. Definition of Done

A ticket is done only when **all** of these are true:

1. It builds and runs locally without errors.
2. It meets every acceptance criterion, not "close enough".
3. No secrets or passwords were committed as part of it.
4. The relevant Absolute Rules from Document 3 are met.
5. It was tested by hand against at least one edge case, not just the happy path.
6. It was checked against Document 1, and nothing extra was added beyond the ticket.
7. A person reviewed it before it was merged, not pasted straight from the AI into the live app.

---

## 4. Build order

Decide the order yourself. Don't let the AI choose it.

1. **Foundation:** login (if any), environment setup, core data model.
2. **The main journey:** the one thing the product must do to be useful at all.
3. **Secondary features.**
4. **Polish:** edge cases, error states, finishing touches.

---

## 5. Ticket backlog

| ID | Title | Priority | Status |
|---|---|---|---|
| AUTH-01 | [Title] | Must | Not started |
