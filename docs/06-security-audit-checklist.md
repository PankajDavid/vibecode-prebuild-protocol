# Document 6 of 6 — Security Audit Checklist

> **Document 3 says what should be built. This checks what actually was.**

| | |
|---|---|
| **Product** | [Product name] |
| **Audited by** | [Your name + which AI tool(s)] |
| **Date** | [Date] |
| **Code version** | [Commit or release] |

> ⚠️ **An AI audit catches common mistakes. It is not a professional security audit and it is not a guarantee.** If your app handles payments, health data, children's data, or other people's personal data at scale, get a human security review before launch.

**How to run it:** paste `prompts/03-audit-before-shipping.md` into your AI tool. For a stronger check, use a **different** AI from the one that wrote the code. An AI is bad at finding its own mistakes.

---

## Part 1 — The checklist

Mark each item **Pass**, **Fail** or **N/A**, with the file that proves it. "Pass" with no file isn't a pass.

### Secrets
| # | Check | Doc 3 rule | Result | Proof (file) |
|---|---|---|---|---|
| S1 | No API keys, passwords or tokens anywhere in the code or Git history | 1 | | |
| S2 | No secrets in browser code (search the built frontend for key names) | 8, 11 | | |
| S3 | No secrets or personal data written to logs | 8 | | |

### Access
| # | Check | Doc 3 rule | Result | Proof |
|---|---|---|---|---|
| A1 | Every endpoint needs login, or is a listed exception, or the app is no-login and rate-limited | 2 | | |
| A2 | Every page/API that loads a record checks the record belongs to this user (try changing an ID in the URL) | 3 | | |
| A3 | Every write action re-checks permission on the server | 3 | | |
| A4 | Organisations' data kept apart in code **and** database, if several share the app | 3 | | |

### Login (skip if no login)
| # | Check | Doc 3 rule | Result | Proof |
|---|---|---|---|---|
| L1 | Passwords hashed with bcrypt (≥12 rounds) or argon2, with a length cap | 5 | | |
| L2 | Login tokens expire in ≤15 minutes; refresh tokens change on use | — | | |
| L3 | Login errors are generic | — | | |
| L4 | Login cookies are HttpOnly, Secure and SameSite | — | | |

### Inputs and money
| # | Check | Doc 3 rule | Result | Proof |
|---|---|---|---|---|
| I1 | Every input checked on the server | 6 | | |
| I2 | Database queries parameterised (no string-built SQL) | 6 | | |
| I3 | Prices, discounts and permissions recalculated on the server | — | | |
| I4 | Webhook signatures verified against the raw body before parsing | 4 | | |
| I5 | CORS is an explicit list, not `*` | — | | |
| I6 | Rate limits on public, login and AI endpoints, and they survive a server restart | — | | |

### AI features (skip if none)
| # | Check | Doc 3 rule | Result | Proof |
|---|---|---|---|---|
| X1 | AI output shown as plain text, never raw HTML, never run as code or used in a query | 10 | | |
| X2 | AI API key only on the server | 11 | | |
| X3 | Per-user AI usage limit in place | 11 | | |
| X4 | Uploads checked for type and size on the server before going to the AI | 6 | | |
| X5 | Spending alert set with the AI provider | — | | |

### Before launch
| # | Check | Doc 3 rule | Result | Proof |
|---|---|---|---|---|
| P1 | Library security scan run (e.g. `npm audit`), serious issues fixed or logged | 7 | | |
| P2 | Every access-control or payment fix has a test | 9 | | |
| P3 | A backup restore has actually been tested | — | | |
| P4 | Compliance section of Document 3 filled in honestly | — | | |

### Optional — only if it applies
- **India (DPDP Act):** consent is recorded before personal data is collected; users can request deletion.
- **Payments:** card details never touch your server (the payment provider handles them).
- **Health or children's data:** stop here and get a professional review.

---

## Part 2 — The verification gate

**Never fix an audit finding until it passes all three questions.** AI reviewers regularly flag problems that aren't there. Fixing those wastes time and can break working code.

| Question | If the answer is no |
|---|---|
| **1. Can you point to the exact file and line?** | Not a finding yet. Ask the AI to show it, or drop it. |
| **2. Does it actually apply to this app?** (e.g. a "weak password" warning in an app with no passwords) | Drop it. |
| **3. Is it a real problem, or only a theoretical one?** | **Real:** fix it now. **Theoretical:** log it in Document 3, Section 9, with a fix-by date. |

Record each finding:

| # | Finding | File:line | Q1 | Q2 | Q3 (Real / Theoretical) | Decision |
|---|---|---|---|---|---|---|
| 1 | | | | | | Fix / Log / Drop |

---

## Part 3 — Sign-off

- [ ] Every checklist item is Pass, N/A, or logged as a Known Deviation.
- [ ] Every Real finding is fixed and re-checked.
- [ ] I understand this is not a professional security audit.

| Name | Date | Signed off |
|---|---|---|
| | | ☐ |
