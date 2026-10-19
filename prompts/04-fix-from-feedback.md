# Prompt 4 — Fix from feedback (the improvement loop)

Use this whenever someone scores or reviews your work: a hackathon judge, a client, an AI evaluator, a code reviewer.

**The loop:** submit early → read the feedback line by line → fix *only* the weaknesses → audit → resubmit.

In a one-day hackathon, this loop took an app from **91.55 → 96.5 → 100**. It works because you stop guessing what to improve and fix exactly what the reviewer marked down.

---

### Step 1 — Fix the weaknesses

```
My submission scored [score]. Here is the full feedback:
[paste every category, its score, and each weakness exactly as written]

Scoring weights (if known): [e.g. Code Quality 20%, Security 15%...]

For each weakness:
1. Explain in plain English what the reviewer is complaining about.
2. Make the smallest change that fixes it.
3. Name the file that proves it's fixed.

Rules: no new features, no redesign, nothing the feedback didn't mention. Start with the weakness in the highest-weighted category.
```

### Step 2 — Check the fixes before resubmitting

Run this in a **different** AI:

```
Check this repo against the feedback it received: [repo link]

Previous feedback:
[paste weaknesses]

PART 1 — For each weakness, answer FIXED / PARTLY FIXED / NOT FIXED and name the file that proves it.
PART 2 — Did the changes break or weaken anything else? Table only: # | Severity | File:line | Problem | Exact fix.

Only report problems you can point to in the code. Mark anything uncertain "Unverified".
```

### Step 3 — Verify, then resubmit
Put every Step 2 finding through the verification gate in Document 6, Part 2. Fix the real ones, retest by hand, and resubmit.

**Know when to stop.** When every category scores high and the remaining points are spread thinly, more changes risk breaking something that works. Stop and protect what you have.
