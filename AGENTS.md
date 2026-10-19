# Rules for AI coding tools working in this project

This project follows the Vibecode Pre-Build Protocol. Read these rules before doing anything else.

## Before writing any code
1. Read every file in `docs/` that has been filled in. If a document still contains `[placeholder]` text, it isn't approved yet — ask the human before relying on it.
2. If `docs/05-feature-tickets.md` has no tickets yet, do not write production code. Help the human finish the documents first.

## While building
3. Build **one ticket at a time**. Only change files that the current ticket needs. If you think another change is needed, say so and stop — don't make it.
4. Do not add features, screens, libraries or services that aren't in the documents. If something is missing from the documents, ask.
5. Every ticket must meet its acceptance criteria and the Definition of Done in `docs/05-feature-tickets.md`.
6. If a decision in `docs/02-technical-architecture.md` seems wrong, explain why and ask. Never silently reverse a written decision.

## Absolute rules — never break these
7. Never put secrets, API keys or passwords in code, in the browser, in logs, or in any Git commit. Use environment variables.
8. Check every user input on the server, even if the screen already checks it.
9. Every write action re-checks on the server that this user is allowed to do it.
10. A user can only ever read or change their own data (or their own organisation's data).
11. Prices, discounts and permissions are always calculated on the server, never trusted from the browser.
12. Treat AI model output as untrusted text: never insert it as raw HTML, never run it as code, never put it directly into a database query.
13. AI API keys stay on the server. Every AI feature has a per-user usage limit.
14. Rate-limit every public endpoint, and especially login and AI endpoints.

## When something is unclear
15. Ask one specific question rather than guessing. A wrong guess costs more than a question.
16. If you can't meet a rule, stop and say which rule and why. The human decides whether to log it as a Known Deviation in `docs/03-security-and-access.md`.
