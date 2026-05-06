---
name: weekly-checkin
description: Monday commits + Friday celebrations cadence that keeps OKRs alive. Asks confidence levels, top priorities, and celebrates wins. Set-and-forget kills OKRs.
version: "1.0.0"
author: okr.io
license: Apache-2.0
---

# Weekly Check-in

The weekly cadence IS the OKR system. Without it, OKRs become quarterly PowerPoint that disconnects from daily work.

## The Cadence

```
MONDAY                           FRIDAY
─────────────────────────────────────────────────
Monday Commits                   Friday Celebrations
"What will I do                  "What was awesome
this week to move                this week?"
our KRs?"
```

After a few weeks of check-ins, you don't need to look up your OKRs - they're just how you think.

## Monday Commits

Ask these questions every Monday:

### 1. Confidence Check

For each KR, what's your confidence level (1-5)?

| KR | Last Week | This Week | Trend |
|----|-----------|-----------|-------|
| KR1: Retention 35%→50% | 3 | 2 | ↓ at risk |
| KR2: Time-to-value 3d→4h | 4 | 4 | → on track |
| KR3: NPS 32→55 | 3 | 4 | ↑ improving |

### 2. Top 3 Priorities

What are you doing THIS WEEK to move the KRs?

- P1: [specific action tied to a KR]
- P2: [specific action tied to a KR]
- P3: [specific action tied to a KR]

**No more than 3.** If you have 10 priorities, you have zero priorities.

### 3. Last Week's Results

What did you try last week and what happened?

- Tried X → moved KR1 by +2pp ✓
- Tried Y → no visible impact ✗
- Blocked on Z → need help

### 4. Blockers

What's preventing progress?

- [blocker] - need [specific help]

## Friday Celebrations

End the week by celebrating wins. This sounds soft but has outsized impact.

Ask: "What was the most awesome thing that happened this week?"

- In engineering?
- In marketing/growth?
- For you personally?

**Why it matters:** People feel part of something special. Morale compounds. The research shows teams that celebrate small wins maintain momentum through hard quarters.

## Output Format

```markdown
# Weekly Check-in: [Date]

## Confidence Levels

| KR | Confidence | Trend | Notes |
|----|------------|-------|-------|
| KR1: [name] | 3/5 | ↓ | at risk, need to pivot approach |
| KR2: [name] | 4/5 | → | on track |
| KR3 (guardrail): [name] | 5/5 | → | holding |

## This Week's Priorities

1. **[Action]** → expected to move KR1
2. **[Action]** → expected to move KR2
3. **[Action]** → expected to move KR1

## Last Week's Results

| Action | KR | Result |
|--------|-----|--------|
| [what we did] | KR1 | +2pp, continue |
| [what we did] | KR2 | no impact, stop |

## Blockers

- [blocker]: need [specific help from who]

## Friday Wins

- 🎉 [awesome thing in engineering]
- 🎉 [awesome thing in growth]
- 🎉 [personal win]
```

## At-Risk Protocol

When confidence drops to 2 or below:

1. Name the specific reason
2. Identify what would need to change
3. Decide: pivot approach, get help, or acknowledge the miss early

**Catching problems at week 4 is better than discovering them at week 12.**

## Anti-Patterns

**No check-ins** - OKRs become quarterly theater

**Too many priorities** - If everything is P1, nothing is

**Status updates without confidence** - "We're working on it" isn't a check-in

**Skipping celebrations** - Morale compounds; don't skip the wins

**Punishing honesty** - If people fear low confidence ratings, they'll lie

## Integration with okr.io

Weekly check-ins in okr.io:
- Update KR confidence levels
- Log priorities and results
- Populate the activity feed
- Feed into end-of-cycle grading

The check-in is the atomic unit of the OKR operating system.
