# Document 2 of 6 — Technical Architecture

> **The tools, the data, and the reason behind every structural decision.**

| | |
|---|---|
| **Product** | [Product name] |
| **Prepared by** | [Your name] |
| **Date** | [Date] |
| **Status** | Draft — pending approval |

**Needs:** an approved Document 1.

**Why reasons matter:** every decision below must say *why*. A decision without a written reason is one the AI will quietly undo three sessions later, because it doesn't remember why you chose it.

---

## 1. Decision log

| Decision | Choice | Why (and what you rejected) |
|---|---|---|
| Overall structure | [One app / one app split into clear modules / separate services] | Start with one app. Only split it if you can name the problem splitting solves. |
| [Decision] | [Choice] | [Reason + rejected alternative] |

---

## 2. How a request moves through the system

One paragraph: what happens from the moment a user taps a button to the moment they see the result: browser → server → database (and AI model, if used) → back. If you can't explain it in one paragraph, it's too complicated for a first version.

[Write here]

---

## 3. Tools and services

| Layer | Choice | Why |
|---|---|---|
| Frontend (what users see) | [e.g. Next.js, React] | |
| Backend (server logic) | [e.g. Next.js API routes, Express] | |
| Database | [e.g. Postgres] | [If several businesses share it, how is their data kept apart?] |
| Hosting | [e.g. Railway, Vercel] | |
| Login | [e.g. Clerk, Supabase Auth, custom, **or none — say why**] | |
| Payments | [If applicable] | |
| File storage | [If applicable] | |
| Live updates | [Sockets / polling / none] | |
| **AI model** | [Provider + model, if applicable] | [Why this one, and what happens if it's slow or down] |

---

## 4. Data model

The main things your app stores and how they connect. Column-level detail can go in a separate schema file the AI reads directly.

| Thing stored | Key fields | Connects to | Notes |
|---|---|---|---|
| [e.g. Order] | [id, ...] | [belongs to a Restaurant] | [e.g. scoped to one restaurant] |

---

## 5. Outside services

| Service | What it does for you | If it goes down | Who owns the account and keys |
|---|---|---|---|
| [Service] | [Purpose] | [App keeps working without it / app stops] | [Name] |

---

## 6. Environments
- Separate **local**, **staging** (test) and **production** (live) setups. Never build against live customer data.
- All secrets and API keys live in environment variables or a secrets manager — never in the code or the repo.
- Staging should match production closely enough that "it worked on staging" actually means something.

---

## 7. Load and performance
- Expected users at launch and in 12 months (rough is fine — 100 or 100,000?):
- The first thing likely to slow down, and the plan for when it does:
- **If you use AI:** expected AI calls per day, rough monthly cost, and what you'll cache to keep cost down:

---

## 8. Deployment
- What triggers a deploy (e.g. pushing to the main branch):
- How you'll undo a bad deploy:
- Backups: how often, and have you actually tested restoring one?

---

## 9. Risks and open questions

| Risk or question | What happens if it's not resolved | Owner |
|---|---|---|
| [Risk] | [Impact] | [Name] |
