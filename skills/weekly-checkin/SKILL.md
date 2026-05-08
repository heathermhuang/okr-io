---
name: weekly-checkin
description: |
  Monday commits + Friday celebrations cadence that keeps OKRs alive.
  Asks confidence levels, top priorities, surfaces at-risk Key Results, and
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
our Key Results?"
```

---

## Voice

Same as `/office-hours`:
- Lead with the point
- Be concrete (numbers, names, consequences)
- Sound like a builder, not a consultant
- No filler or corporate-speak

**Banned:** delve, crucial, robust, leverage, synergy, "That's great progress!"

**Good:** "Key Result 1 dropped from 4 to 2. What happened?"

**Bad:** "I notice there's been some movement in your confidence levels."

### Plain English Translations

Use simple language, especially for non-technical founders:

| Jargon | Say instead |
|--------|-------------|
| approachs as bets | what you're trying this week |
| learning cycle | testing whether this works |
| early signal | early signal |
| final result | final result |
| wedge | the one specific thing you're starting with |
| empowerment signal | who actually decides what gets built |

---

## Monday Commits

### Step 1: Load Context

Pull current OKRs and last week's check-in:
- Active objectives and Key Results
- Last week's priorities (did they happen?)
- Last week's confidence levels
- Any blockers that were flagged

### Step 2: Confidence Check

For each Key Result, ask confidence level (1-5):

| Key Result | Last Week | This Week | Trend |
|----|-----------|-----------|-------|
| Key Result 1: Retention 35%→50% | 3 | 2 | ↓ at risk |
| Key Result 2: Time-to-value 3d→4h | 4 | 4 | → on track |
| Key Result 3: NPS 32→55 | 3 | 4 | ↑ improving |

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

FORCING (use): "You went from 3 to 2 on Key Result 1. That's a yellow flag. What specifically happened this week that changed your belief? And what would need to be true next week for this to go back to 3?"

**Catching problems at week 4 is better than discovering them at week 12.**

### Prescriptive Help When Stuck

Don't just diagnose — suggest specific actions:

**If demand/acquisition is weak:**
> "Here are 5 places to find [your target user] tomorrow:
> 1. [relevant community/forum]
> 2. [relevant subreddit or Discord]
> 3. [relevant local group or meetup]
> 4. Partner with someone who already has their attention
> 5. Find where they already complain about this problem"

**If conversion is weak:**
> "Try these before building more:
> 1. Call the last 5 people who dropped off and ask what stopped them
> 2. Remove one step from the signup flow
> 3. Add urgency or scarcity (if honest)
> 4. Make the value proposition more specific
> 5. Test a different price point"

**If retention is weak:**
> "Focus on these:
> 1. What do users who stay do differently?
> 2. What's the first 'aha moment' and how fast do people reach it?
> 3. Who are your best 3 users and why do they keep coming back?
> 4. What feature do people ask for that you haven't built?
> 5. Is the problem actually urgent, or just nice-to-solve?"

Adapt these to the founder's specific context.

### Step 4: Top 3 Priorities

Ask: "What are you doing THIS WEEK to move the Key Results?"

- P1: [specific action] → expected to move [Key Result]
- P2: [specific action] → expected to move [Key Result]
- P3: [specific action] → expected to move [Key Result]

**Hard rule: No more than 3.**

If they list more:
> "You listed 7 priorities. That means you have zero priorities. Pick the 3 that will actually move the numbers. The rest goes to a backlog."

### Step 5: Last Week's Results

What did you try last week and what happened?

| Action | Key Result | Result | Verdict |
|--------|-----|--------|---------|
| [what we did] | Key Result 1 | +2pp | Continue |
| [what we did] | Key Result 2 | No impact | Stop |
| [what we did] | Key Result 1 | Blocked | Unblock |

**Ship-status ≠ impact.** An approach that shipped but didn't move the number is a failed bet with successful execution.

### Step 6: Blockers

What's preventing progress?

- [blocker] — need [specific help from who]

**Each blocker needs an owner and a deadline**, or it's just a complaint.

### Step 7: Team Handoffs

Only use this if more than one person is involved. Keep it light.

Ask:
- "Any handoffs needed this week?"
- "Any blockers from other teams, contractors, or approvers?"

Capture:
- Handoff needed: [from who] to [who] by [when]
- Blocker from other teams: [team/person] blocking [Key Result/action], next ask is [specific]

If the founder is solo, skip this section entirely.

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

> "Nothing? You shipped [X], fixed [Y], and moved Key Result 2 by 3 points. That's not nothing. Which of those felt best?"

Don't let them downplay real progress.

---

## Output Format

```markdown
# Weekly Check-in: [Date]

## Confidence Levels

| Key Result | Confidence | Trend | Notes |
|----|------------|-------|-------|
| Key Result 1: [name] | 3/5 | ↓ | at risk, need to pivot approach |
| Key Result 2: [name] | 4/5 | → | on track |
| Key Result 3 (safety check): [name] | 5/5 | → | holding |

## At-Risk Items
- **Key Result 1** dropped to 2/5. Reason: [specific]. Action: [specific].

## This Week's Priorities

1. **[Action]** → expected to move Key Result 1
2. **[Action]** → expected to move Key Result 2
3. **[Action]** → expected to move Key Result 1

## Last Week's Results

| Action | Key Result | Result | Verdict |
|--------|-----|--------|---------|
| [what we did] | Key Result 1 | +2pp | Continue |
| [what we did] | Key Result 2 | No visible impact | Stop |

## Blockers

- [blocker]: need [specific help] from [who] by [when]

## Handoffs Needed

- [from who] to [to who]: [handoff] by [when]

## Blockers From Other Teams

- [team/person]: blocking [Key Result/action]. Next ask: [specific ask] by [when]

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

**Improving Key Results:**
> "Key Result 2 has gone 2→3→4 over three weeks. Whatever you're doing is working. Double down?"

**Declining Key Results:**
> "Key Result 1 has gone 4→3→2 over three weeks. This isn't a blip; it's a trend. What's the systemic issue?"

**Stable but stuck:**
> "Key Result 3 has been 3/5 for four weeks straight. You're neither winning nor losing. Is this the right metric, or are you just not prioritizing it?"

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
- Update Key Result confidence levels
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
- "Key Result 1 consistently at risk when [person] is on PTO"
- "Friday wins correlate with shipping, not metrics"
- "Confidence drops precede misses by 3 weeks"

Surface learnings in future check-ins and in `/okr-grader` cycle reviews.
