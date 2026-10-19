# Document 4 of 6 — Frontend Specification

> **Every screen, every flow, and every state a component can be in, decided before it's built.**

| | |
|---|---|
| **Product** | [Product name] |
| **Prepared by** | [Your name] |
| **Date** | [Date] |
| **Status** | Draft — pending approval |

Ask an AI to "build the dashboard" and it will build *a* plausible dashboard. This document removes the guessing.

---

## 1. Screens

| Screen | What the user gets done here | Who can open it |
|---|---|---|
| [Screen name] | [Purpose] | [Anyone / logged-in users / admins] |

---

## 2. Main user journeys

Write the steps, **including what happens when something goes wrong**, not just the happy path.

### [Journey name, e.g. "First-time sign-up"]
1. [Step]
2. [Step]
3. [Step — including the error or exit path]

### [Journey name, e.g. "The main thing users come to do"]
1. [Step]
2. [Step]
3. [Step]

---

## 3. Component states

Every interactive part of the screen needs all of these defined **before** it's built, not discovered by a user after launch.

| State | What it means | What the user sees |
|---|---|---|
| Loading | Waiting for data | [Skeleton / spinner] |
| Empty | No data yet, and that's normal | [Friendly message + what to do next] |
| Error | Something failed | [Plain-language message + a retry button] |
| Populated | Normal, with data | [Description] |

**If the screen uses AI, add three more:**

| State | What it means | What the user sees |
|---|---|---|
| AI thinking | Waiting for the AI (can take several seconds) | [Progress message; the button is disabled so it can't be pressed twice] |
| AI unavailable | AI provider down, slow, or usage limit reached | [Plain message, and what still works without AI] |
| AI doesn't know | The AI correctly refused to guess | [Honest message + where to get the answer instead] |

---

## 4. Screen sizes and devices
- Mobile-first or desktop-first? [Choice + why — who are your users and what device do they hold?]
- Breakpoints: [e.g. phone / tablet / desktop]
- Slow or no internet: [What happens? Does anything work offline?]

---

## 5. Accessibility
- Text contrast meets the minimum ratio (WCAG AA) everywhere.
- Everything can be used with a keyboard alone.
- Icon-only buttons and form fields have labels screen readers can read.
- Every focusable element shows a visible focus outline.
- **For less tech-confident users:** large tap targets, plain words, and their own language where possible.

---

## 6. Design rules
- Spacing scale: [e.g. multiples of 4px]
- Fonts and text sizes: [Choices]
- Colours: named tokens (e.g. `primary`, `danger`) used everywhere, not raw colour codes scattered through the code
- Reuse existing components before creating new ones. The AI must flag any new component before building it.
