---
name: weekly-checkin
description: |
  Monday commits + Friday celebrations cadence that keeps OKRs alive.
  Asks confidence levels, top priorities, surfaces at-risk KRs, and
  celebrates wins. Set-and-forget kills OKRs; this skill prevents that.
version: "2.0.0"
author: okr.io
license: Apache-2.0
triggers:
  - weekly checkin
  - monday commits
  - friday wins
  - how are OKRs going
---

# Weekly Check-in

The weekly cadence IS the OKR system. Without it, OKRs become quarterly PowerPoint that disconnects from daily work.

After a few weeks of check-ins, you don't need to look up your OKRs — they're just how you think.

---

## The Cadence

```
MONDAY                           FRIDAY
─────────────────────────────────────────────────
Monday Commits                   Friday Celebrations
"What will I do                  "What was awesome
this week to move                this week?"
our KRs?"
```

---

## Voice

Same as `/office-hours`:
- Lead with the point
- Be concrete (numbers, names, consequences)
- Sound like a builder, not a consultant
- No filler or corporate-speak

**Banned:** delve, crucial, robust, leverage, synergy, "That's great progress!"

**Good:** "KR1 dropped from 4 to 2. What happened?"

**Bad:** "I notice there's been some movement in your confidence levels."

---

## Monday Commits

### Step 1: Load Context

Pull current OKRs and last week's check-in:
- Active objectives and KRs
- Last week's priorities (did they happen?)
- Last week's confidence levels
- Any blockers that were flagged

### Step 2: Confidence Check

For each KR, ask confidence level (1-5):

| KR | Last Week | This Week | Trend |
|----|-----------|-----------|-------|
| KR1: Retention 35%→50% | 3 | 2 | ↓ at risk |
| KR2: Time-to-value 3d→4h | 4 | 4 | → on track |
| KR3: NPS 32→55 | 3 | 4 | ↑ improving |

**Interpretation:**
- 5 = Will definitely hit
- 4 = On track, no concerns
- 3 = Possible, need things to go right
- 2 = At risk, need intervention
- 1 = Will miss without major change

### Step 3: At-Risk Protocol

When confidence drops to 2 or below, **STOP** and dig in:

1. **Name the specific reason** — not "it's hard" but "we lost 2 days to [X]"
2. **Identify what would need to change** — resource, scope, approach?
3. **Decide:** pivot approach, get help, or acknowledge miss early

**Pushback pattern:**

SOFT (avoid): "What's causing the confidence drop?"

FORCING (use): "You went from 3 to 2 on KR1. That's a yellow flag. What specifically happened this week that changed your belief? And what would need to be true next week for this to go back to 3?"

**Catching problems at week 4 is better than discovering them at week 12.**

### Step 4: Top 3 Priorities

Ask: "What are you doing THIS WEEK to move the KRs?"

- P1: [specific action] → expected to move [KR]
- P2: [specific action] → expected to move [KR]
- P3: [specific action] → expected to move [KR]

**Hard rule: No more than 3.**

If they list more:
> "You listed 7 priorities. That means you have zero priorities. Pick the 3 that will actually move the numbers. The rest goes to a backlog."

### Step 5: Last Week's Results

What did you try last week and what happened?

| Action | KR | Result | Verdict |
|--------|-----|--------|---------|
| [what we did] | KR1 | +2pp | Continue |
| [what we did] | KR2 | No impact | Stop |
| [what we did] | KR1 | Blocked | Unblock |

**Ship-status ≠ impact.** An initiative that shipped but didn't move the number is a failed bet with successful execution.

### Step 6: Blockers

What's preventing progress?

- [blocker] — need [specific help from who]

**Each blocker needs an owner and a deadline**, or it's just a complaint.

---

## Friday Celebrations

End the week by celebrating wins. This sounds soft but has outsized impact.

### Why It Matters

- People feel part of something special
- Morale compounds
- Teams that celebrate small wins maintain momentum through hard quarters
- It's also a forcing function to notice what's working

### The Question

Ask: "What was the most awesome thing that happened this week?"

Categories to prompt:
- In engineering/product?
- In marketing/growth?
- For a specific user?
- For you personally?

### Anti-Pattern: Skipping Wins

If someone says "nothing really" or skips:

> "Nothing? You shipped [X], fixed [Y], and moved KR2 by 3 points. That's not nothing. Which of those felt best?"

Don't let them downplay real progress.

---

## Output Format

```markdown
# Weekly Check-in: [Date]

## Confidence Levels

| KR | Confidence | Trend | Notes |
|----|------------|-------|-------|
| KR1: [name] | 3/5 | ↓ | at risk, need to pivot approach |
| KR2: [name] | 4/5 | → | on track |
| KR3 (guardrail): [name] | 5/5 | → | holding |

## At-Risk Items
- **KR1** dropped to 2/5. Reason: [specific]. Action: [specific].

## This Week's Priorities

1. **[Action]** → expected to move KR1
2. **[Action]** → expected to move KR2
3. **[Action]** → expected to move KR1

## Last Week's Results

| Action | KR | Result | Verdict |
|--------|-----|--------|---------|
| [what we did] | KR1 | +2pp | Continue |
| [what we did] | KR2 | No visible impact | Stop |

## Blockers

- [blocker]: need [specific help] from [who] by [when]

## Friday Wins

- 🎉 [awesome thing]
- 🎉 [awesome thing]
- 🎉 [personal win]

---
*Week N of Q2 2026*
*Next check-in: [date]*
```

---

## Trend Analysis

After 3+ weeks, surface patterns:

**Improving KRs:**
> "KR2 has gone 2→3→4 over three weeks. Whatever you're doing is working. Double down?"

**Declining KRs:**
> "KR1 has gone 4→3→2 over three weeks. This isn't a blip; it's a trend. What's the systemic issue?"

**Stable but stuck:**
> "KR3 has been 3/5 for four weeks straight. You're neither winning nor losing. Is this the right metric, or are you just not prioritizing it?"

---

## Anti-Patterns

**No check-ins**
OKRs become quarterly theater disconnected from work.

**Too many priorities**
If everything is P1, nothing is.

**Status updates without confidence**
"We're working on it" isn't a check-in. Confidence forces honesty.

**Skipping celebrations**
Morale compounds. Don't skip the wins.

**Punishing honesty**
If people fear low confidence ratings, they'll lie. Create safety.

**All-green syndrome**
If confidence is always 4-5, either targets are too easy or people are afraid to flag risk.

---

## Integration with okr.io

Weekly check-ins:
- Update KR confidence levels
- Log priorities and results
- Populate the activity feed
- Feed into end-of-cycle grading (`/okr-grader`)
- Surface in MCP context for coding agents

The check-in is the atomic unit of the OKR operating system.

---

## Learnings Capture

After each check-in, note patterns:

```json
{
  "type": "checkin_learning",
  "date": "[timestamp]",
  "pattern": "[what we noticed]",
  "implication": "[what to do differently]"
}
```

Examples:
- "KR1 consistently at risk when [person] is on PTO"
- "Friday wins correlate with shipping, not metrics"
- "Confidence drops precede misses by 3 weeks"

Surface learnings in future check-ins and in `/okr-grader` cycle reviews.
