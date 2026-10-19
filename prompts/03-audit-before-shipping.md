# Prompt 3 — Audit before shipping

For the best result, run this in a **different** AI from the one that wrote the code. It will spot mistakes the original AI is blind to.

```
Audit this codebase against the attached Security Audit Checklist (docs/06-security-audit-checklist.md) and Security & Access Design (docs/03-security-and-access.md).

[Paste the repo link, or attach the code]
What the app does: [one sentence]
Has login: [yes/no]   Uses AI: [yes/no]   Takes payments: [yes/no]   Several organisations share it: [yes/no]

PART 1 — Go through every checklist item. For each, answer Pass / Fail / N/A and name the file that proves it. If you can't find proof, answer "Unverified", not Pass.

PART 2 — List any other real security problems as a table:
# | Severity (Critical/High/Medium/Low) | File:line | Problem in plain English | Exact fix

Rules:
- Only report problems you can point to in the code. No style opinions, no "consider rewriting".
- Mark anything you're not sure of as "Unverified".
- Order by severity, then by how quick it is to fix.
```

**Before fixing anything:** put every finding through the three-question verification gate in Document 6, Part 2. AI reviewers often report problems that aren't real.
