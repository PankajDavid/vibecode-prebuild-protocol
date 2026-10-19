# Vibecode Pre-Build Protocol

**Plan before you prompt.** Six free documents that stop AI coding tools from building the wrong thing, the unsafe thing, or a thing nobody can maintain.

🎥 **[Watch the 5-minute walkthrough](https://www.youtube.com/watch?v=jjwpRMOP-Lg)**: how a feedback loop and these documents took a hackathon entry from 91.55 to 100/100.

Works with Claude Code, Cursor, Windsurf, Lovable, Bolt, Replit, GitHub Copilot, ChatGPT and Gemini.

By **Pankaj David** · [Vibecode with Pankaj on YouTube](https://www.youtube.com/@vibecodewithpankaj)

---

## Why this exists

Most AI-built apps break for one of three reasons:

1. **The AI guessed what you wanted.** You said "build a dashboard" and got *a* dashboard, not *your* dashboard.
2. **The AI optimised for "it runs", not "it's safe".** Secrets in the code, no rate limits, users able to see each other's data.
3. **You asked for too much in one prompt.** The AI changed ten files at once and broke three things you didn't notice.

These documents fix all three. You write down what you want, how it's built and what's never allowed *before* the AI writes code. Then the AI builds one small ticket at a time against those rules.

---

## What's inside

| File | What it's for |
|---|---|
| `docs/01-product-requirements.md` | What you're building, for whom, and what you're **not** building |
| `docs/02-technical-architecture.md` | Which tools and services you'll use, and why |
| `docs/03-security-and-access.md` | The rules the AI is never allowed to break |
| `docs/04-frontend-specification.md` | Every screen, and what it shows when loading, empty or broken |
| `docs/05-feature-tickets.md` | Your build broken into small pieces the AI builds one at a time |
| `docs/06-security-audit-checklist.md` | The check you run before anything goes live |
| `prompts/` | Copy-paste prompts for filling the documents, building, auditing and fixing |
| `AGENTS.md` / `CLAUDE.md` | Rules your AI coding tool reads automatically |

---

## How to use it (3 steps)

**Not on GitHub?** Click the green **Code** button above → **Download ZIP** → unzip it.

### Step 1 — Copy it into your project
Put the `docs/`, `prompts/`, `AGENTS.md` and `CLAUDE.md` into your project folder. Your AI coding tool will now read the rules automatically.

### Step 2 — Fill in the documents, one at a time
Open `prompts/01-fill-documents.md`, paste the prompt into your AI tool with your idea, and let it fill **Document 1 only**. Read it. Fix anything wrong. Then move to Document 2. Don't let the AI do all five at once — each one builds on the last.

### Step 3 — Build one ticket at a time, then audit
Use `prompts/02-build-a-ticket.md` for each ticket in Document 5. When everything's built, run `prompts/03-audit-before-shipping.md`. If you get feedback (from a hackathon judge, a client or a reviewer), use `prompts/04-fix-from-feedback.md`.

---

## When to use the full process, and when not to

- **Real product, real users, real money:** all six documents. No exceptions.
- **Hackathon or one-day build:** skip to a one-page version of Document 1, keep Document 3's Absolute Rules, and use the feedback loop in `prompts/04-fix-from-feedback.md`. That loop is what took my hackathon entry from 91.55 to 100.
- **Throwaway experiment:** just keep the Absolute Rules in `AGENTS.md`.

---

## Important

An AI audit catches common mistakes. **It is not a professional security audit and it is not a guarantee.** If your app handles payments, health data, children's data or other people's personal information at scale, get a human security review before launch.

---

## Licence

[CC BY 4.0](LICENSE). Use it, change it, share it, use it commercially. Just credit **Pankaj David / [Vibecode with Pankaj](https://www.youtube.com/@vibecodewithpankaj)** with a link back to this repo.

Copyright © 2026 Pankaj David. This material is provided as is, without warranty, and is not a professional security audit or legal or compliance advice.
