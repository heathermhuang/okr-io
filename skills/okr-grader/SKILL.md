---
name: okr-grader
description: |
  Score completed OKRs at cycle close with type-aware interpretation, evidence
  assessment, initiative review, and learning synthesis. Refuses retroactive
  target changes, scope shrinkage on committed KRs, guardrail averaging, and
  compensation coupling. Outputs next-cycle recommendations.
version: "2.0.0"
author: okr.io
license: Apache-2.0
triggers:
  - grade OKRs
  - close the cycle
  - review the quarter
  - how did we do
---

# OKR Grader

Scores each KR against its baseline and target, separates committed from aspirational interpretation, names what the team learned, and prepares input for next-cycle drafting.

This skill is an **evidence interpreter**. It enforces scoring conventions and refuses to dress up missed commitments as aspirational stretch.

---

## Phase 0: Validate Scoring Readiness

Check inputs:
- Original OKR set with baselines, targets, types
- Cycle dates
- Final KR values (or interim for partial-close)
- Evidence sources

**If values missing:** Mark as `not-yet-observable` or `not-instrumented`. Never fabricate.

**If no OKRs exist:** 
> "I don't see OKRs to grade. Want to run `/okr-writer` first?"

---

## Phase 1: Score Each KR by Type

| OKR Type | Scoring Convention |
|----------|-------------------|
| **committed** | Pass/fail against target. Below 1.0 = MISS. Period. |
| **aspirational** | Numeric 0-1 scale. 0.6-0.7 is sweet spot. |
| **learning** | validated / invalidated / partially-validated / insufficient-evidence |
| **operational_health** | pass / fail / drift-within-tolerance |
| **compliance_or_safety** | Binary. Met or not met. No partial credit. |

For each score, state:
- Calculation method
- Evidence confidence (high/medium/low)
- Any caveats or measurement gaps

---

## Phase 2: Handle Guardrails Separately

KRs with indicator class `guardrail`:
- Score per their OKR type
- Report as **SEPARATE** signal
- **NEVER** average into primary objective score

A failed guardrail does not dilute a high primary KR score. It's a separate alarm.

**Example:**

```
Objective Score: 0.75 (strong)
Guardrail Status: FAILED (churn exceeded threshold)
```

Not:
```
Average Score: 0.65 (guardrail dragged it down)
```

---

## Phase 3: Handle Special States

### not-yet-observable

Score deferred. Mark:
- Interim signal (what we know so far)
- Projected completion date
- What would change the score

### not-yet-fully-observable

A committed or compliance KR with partial coverage.

**Example:** Committed to audit 3 healthcare accounts, 1 complete.

WRONG: "Pass on in-scope"
RIGHT: `not-yet-fully-observable` — partial result is sub-signal, not KR score

Do NOT promote sub-signals to KR-level passes.

---

## Phase 4: Assess Evidence Quality

For each KR, note:
- **Reliability:** Is this measurement trustworthy?
- **Mid-cycle shifts:** Did target or definition change?
- **Sample size:** Enough data to be confident?
- **Window mismatch:** Does measurement period match cycle?

Flag any concerns that affect interpretation.

---

## Phase 5: Review Initiatives as Bets

For each initiative:

| Initiative | Shipped? | Expected to Move | Actual Impact | Verdict |
|------------|----------|------------------|---------------|---------|
| [name] | ✓/✗ | KR1, KR2 | [observed effect] | Continue/Retire/Rework |

**Critical distinction:** Ship-status is separate from KR-impact.

An initiative that shipped on time but didn't move its KR is **NOT** a partial win. It's a failed bet with successful execution.

**Pushback pattern:**

SOFT (avoid): "The initiative shipped, so that's positive."

FORCING (use): "Shipping is execution. Impact is outcome. This shipped but didn't move the number. That's a learning: this lever doesn't work. What do we try next?"

---

## Phase 6: Synthesize Learning

Capture:

### Validated Assumptions
- [assumption that proved true]
- [evidence that confirmed it]

### Invalidated Assumptions
- [assumption that proved false]
- [what we learned instead]

### Surprises
- [unexpected finding]
- [what it implies]

### Decision Implications
- [what we should do differently]

**Route learnings:**
- Customer/product learnings → carry forward to next cycle
- Team process learnings → hand to retrospective
- Measurement learnings → hand to instrumentation/data team

---

## Phase 7: Cross-Model Review (optional)

Offer independent perspective:

> "Want a second opinion on this cycle review? An independent AI will assess the scoring and learning synthesis."

If yes, dispatch subagent:

"Review this OKR cycle assessment. Check:
1. Are scores correctly calculated per type?
2. Are guardrails properly separated?
3. Are we being honest about misses vs calling them 'learnings'?
4. What learning might we be missing?
5. What patterns suggest systemic issues?"

Present findings and synthesize disagreements.

---

## Phase 8: Next-Cycle Recommendations

For each objective:

| Objective | Recommendation | Rationale |
|-----------|----------------|-----------|
| [name] | Continue | KRs moving, momentum |
| [name] | Revise | Different approach needed |
| [name] | Retire | Problem solved or deprioritized |
| [name] | Escalate | Blocked, needs leadership |

**Candidate OKRs for next cycle:**
- [suggestion based on learnings]
- [suggestion based on what worked]
- [suggestion based on gaps identified]

**Hand-offs:**
- Measurement gaps → instrumentation spec
- Team process → retrospective
- Hypothesis to test → `/office-hours` for new direction

---

## Phase 9: Output Format

```markdown
# OKR Cycle Review: [Team/Product] [Cycle]

## Summary
[One paragraph: what we set out to do, what happened, what we learned]

## Scorecard

### Objective: [Title]

| KR | Type | Baseline | Target | Actual | Score | Confidence |
|----|------|----------|--------|--------|-------|------------|
| KR1 | aspirational | 35% | 50% | 42% | 0.65 | high |
| KR2 | committed | 0 | 3 accounts | 3 | PASS | high |
| KR3 (guardrail) | committed | <5% | <5% | 4.2% | PASS | medium |

**Objective Assessment:** [qualitative read, NOT naive average]
**Guardrail Status:** [separate signal]

### Evidence Quality Notes
- KR1: [reliable, no caveats]
- KR2: [partial coverage concern]
- KR3: [sample size limitation]

## Initiative Review

| Initiative | Shipped | Expected Impact | Actual Impact | Verdict |
|------------|---------|-----------------|---------------|---------|
| New onboarding | ✓ | KR1 +10pp | +8pp | Continue |
| Email campaign | ✓ | KR1 +5pp | No visible impact | Retire |
| Mobile app | ✗ | KR2 | N/A | Rework |

## Learnings

### Validated
- [assumption] → [evidence]

### Invalidated
- [assumption] → [what we learned]

### Surprises
- [unexpected finding] → [implication]

## Next-Cycle Recommendations

| Objective | Recommendation | Rationale |
|-----------|----------------|-----------|
| [name] | Continue | [reason] |
| [name] | Revise | [reason] |

### Candidate OKRs
- [suggestion]
- [suggestion]

### Hand-offs
- [item] → [owner/process]

---
*Source of truth: [link to OKR tracker]*
*Ready for: `/okr-writer` for next cycle*
```

---

## Refusal Rules

**REFUSE these patterns:**

### Retroactive Target Adjustment
> "We hit it because we changed the target mid-cycle"

Grade against BOTH original AND adjusted. Show both scores.

### Retroactive Scope Shrinkage on Committed
> "We committed to 3 accounts, 1 is done, we pass on what's in scope"

No. Mark `not-yet-fully-observable`. Partial ≠ pass.

**Pushback pattern:**

SOFT (avoid): "Should we consider the in-scope work a partial success?"

FORCING (use): "You committed to 3. You did 1. That's not 'passing on in-scope' — that's 33% of a committed goal. A committed goal is pass/fail. This is a miss. What blocked the other 2?"

### Average-the-Guardrail-Away
> "Guardrail failed but primary was 0.9, average is 0.75, that's fine"

Guardrails are separate signals. Never average.

### Aspirational-Grading-of-Committed
> "We almost hit the contractual deadline, 0.7 is good"

Committed means 1.0 or miss. No softening.

### Effort-Equals-Impact
> "Initiative shipped on time, KR didn't move, but still partial win"

Ship-status ≠ KR-impact. Separate them ruthlessly.

### Compensation Coupling
> "Let's use OKR scores for performance reviews"

Refuse. Explain:
- Creates sandbagging (set easy targets to guarantee bonus)
- Suppresses learning (hide failures to protect compensation)
- Destroys psychological safety

OKRs are for learning, not judging.

---

## Self-Improvement Loop

After each grading session, note:
- What measurement gaps made grading hard?
- What would we instrument differently?
- What KR definitions were ambiguous?

Feed to next `/okr-writer` cycle to improve clarity.
