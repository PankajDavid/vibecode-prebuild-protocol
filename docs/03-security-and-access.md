# Document 3 of 6 — Security & Access Design

> **The document most AI-built apps skip, and the one that matters most.**

| | |
|---|---|
| **Product** | [Product name] |
| **Prepared by** | [Your name] |
| **Date** | [Date] |
| **Status** | Draft — pending approval |

AI coding tools optimise for "it runs". They don't optimise for "it's safe to put in front of real users and real money" unless the rules are written down in front of them. This document is those rules.

---

## 1. Login (authentication)

**Does this app need a login?** [Yes / No — and why]

A no-login app is a valid choice: a public tool, a calculator, an app for people who won't create accounts. If you choose no login, write the reason here, and make sure Section 4's rate limits and Section 5's AI limits are in place instead. Without a login, rate limits are your main protection.

If the app has a login:

| Item | Requirement |
|---|---|
| Password storage | bcrypt (at least 12 rounds) or argon2. Never plain text, MD5 or SHA. |
| Session type | [Server session cookie or JWT — say which, and why] |
| How long a login token lasts | 15 minutes or less, with refresh tokens that change each time they're used |
| Password length | At least 8 characters for users; a hard limit (e.g. 128) on the server so huge passwords can't overload it |
| Login error messages | Generic ("Email or password is wrong"), so attackers can't discover which emails have accounts |
| Two-step login (MFA) | Required at least for admin accounts |
| Cookies | HttpOnly, Secure, and SameSite set on every login cookie |

---

## 2. Who can see and do what (authorisation)

| Role | Can access | Can never access |
|---|---|---|
| [Role] | [Scope] | [Explicitly denied] |

**If several businesses or organisations share the app:** keep their data apart in the app's code **and** in the database itself (e.g. Postgres Row-Level Security). One forgotten "only this organisation's data" filter is a full data breach, not a small bug.

**The most common AI-built bug:** changing the number in a URL (`/orders/41` → `/orders/42`) shows someone else's data. Every page and API that loads a record must check that record belongs to this user.

---

## 3. Protecting data
- HTTPS everywhere, no exceptions.
- Database and file storage encrypted at rest (most hosts do this by default — confirm it).
- Secrets and API keys in environment variables or a secrets manager. Never in the repo, never in browser code, never in logs.
- Collect only the personal data the product actually needs.
- Decide how long you keep data and how you delete it **before** launch, not after a user asks.

---

## 4. Inputs and APIs
- Check every input on the server, even if the screen already checks it.
- Use parameterised database queries only. Never build SQL by joining strings.
- Rate-limit every public endpoint, and especially login.
- CORS: an explicit list of allowed websites. Never `*` in production.
- Webhooks (e.g. payment notifications): verify the signature against the raw request body **before** anything reads it as JSON.
- Never trust prices, discounts or permission flags sent from the browser. The server recalculates anything that affects money or access.

---

## 5. AI features (skip if your app has none)

If your app sends anything to an AI model, these apply:

- **AI output is untrusted.** Show it as plain text. Never insert it as raw HTML, never run it as code, never put it directly into a database query or command.
- **The AI API key stays on the server.** The browser talks to your server; your server talks to the AI.
- **Assume users will try to trick the AI.** Someone will type "ignore your instructions and…". Keep your instructions to the AI separate from the user's text, and don't give the AI access to anything a user shouldn't control.
- **Cap AI usage per user** (per minute and per day), so one person, or one bot, can't run up your bill.
- **Set a spending alert** with your AI provider.
- **Check uploads before sending them to the AI:** file type, file size, and nothing sensitive unless the user knowingly sends it.
- **Tell users not to enter sensitive details** (ID numbers, bank details) unless your app genuinely needs them.
- **Let the AI say "I don't know".** For facts that matter (laws, schemes, prices, medical information), give the AI the correct source material and tell it to refuse rather than guess.

---

## 6. Logging and monitoring
- No secrets, tokens or personal data in logs.
- Alerts on repeated failed logins, rate-limit hits, and unusual AI usage.
- A record of privileged actions: role changes, data exports, deletions.

---

## 7. Compliance

Fill this in for your country and your type of data. **Leave it blank rather than guess.** A wrong compliance assumption is worse than an admitted gap.

| Requirement | Applies? | How it's handled |
|---|---|---|
| Where data must be stored (data residency) | [Y/N] | |
| Recording user consent | [Y/N] | |
| Users' right to have data deleted | [Y/N] | |
| Payments rules (e.g. PCI-DSS — usually handled by using a payment provider) | [Y/N] | |
| Health, financial or children's data rules | [Y/N] | |
| **India:** DPDP Act 2023 (consent, purpose limits, deletion) | [Y/N] | |

---

## 8. Absolute rules — non-negotiable

| # | Rule |
|---|---|
| 1 | No secret, API key or password is ever committed to source control, in any commit, on any branch. |
| 2 | Every endpoint requires login by default. Public endpoints are a written exception listed in Section 9. **If the whole app has no login (Section 1), every endpoint is rate-limited instead.** |
| 3 | Every write action re-checks permission on the server, even if the screen already hid the button. |
| 4 | Every webhook verifies its signature against the raw body before reading it. |
| 5 | Every password is hashed with bcrypt or argon2 at the required strength. |
| 6 | Every user input is checked on the server before it reaches a database query or a command. |
| 7 | Every library is checked for known security problems before it goes live. |
| 8 | No sensitive data in browser code, URLs or logs. |
| 9 | Every access-control or payment fix gets a test, so the same bug can't quietly come back. |
| 10 | AI output is never run as code, inserted as HTML, or used directly in a query. |
| 11 | AI API keys never reach the browser, and every AI feature has a per-user limit. |

---

## 9. Known deviations

Any place this project deliberately breaks a rule above, with the reason and a fix-by date. A written, justified exception is a decision. An unwritten one is a vulnerability.

| Rule # | What's different | Why it's acceptable for now | Fix by |
|---|---|---|---|
| [#] | [Deviation] | [Reason] | [Date or milestone] |

---

## 10. Pre-launch security gate

Nothing goes live until every box is ticked, whatever the deadline.

- [ ] Every Absolute Rule is met, or logged in Section 9 with a fix-by date.
- [ ] Library security scan run and reviewed (e.g. `npm audit`).
- [ ] Tested by hand: logged in as one user, tried to open another user's data. It must fail.
- [ ] Rate limits confirmed working on public, login and AI endpoints.
- [ ] Backups confirmed, and one restore actually tested.
- [ ] Document 6 (Security Audit Checklist) completed.
