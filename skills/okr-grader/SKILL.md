---
name: okr-grader
description: Score completed OKRs at cycle close with type-aware interpretation, evidence assessment, and learning synthesis. Refuses retroactive target changes, scope shrinkage on committed KRs, averaging guardrails, and compensation coupling.
version: "1.0.0"
author: okr.io
license: Apache-2.0
---

# OKR Grader

Scores each KR against its baseline and target, separates committed from aspirational interpretation, names what the team learned, and prepares input for next-cycle drafting.

This skill is an evidence interpreter. It enforces scoring conventions and refuses to dress up missed commitments as aspirational stretch.

## Instructions

### 1. Validate Scoring Readiness

Check inputs:
- Original OKR set with baselines, targets, types
- Cycle dates
- Final KR values (or interim for partial-close)
- Evidence sources

If values missing, mark as `not-yet-observable` or `not-instrumented`. Never fabricate.

### 2. Score Each KR by Type

| OKR Type | Scoring Convention |
|----------|-------------------|
| **committed** | Pass/fail against target. Anything below 1.0 is a MISS. |
| **aspirational** | Numeric 0-1 scale. 0.6-0.7 is sweet spot. |
| **learning** | validated / invalidated / partially-validated / insufficient-evidence |
| **operational_health** | pass / fail / drift-within-tolerance |
| **compliance_or_safety** | Binary. Met or not met. No partial credit. |

For each score, state calculation and evidence confidence (high/medium/low).

### 3. Handle Guardrails Separately

KRs with indicator class `guardrail` are:
- Scored per their OKR type
- Reported as a SEPARATE signal
- **NEVER averaged into the primary objective score**

A failed guardrail does not dilute a high primary KR score.

### 4. Handle Special States

**not-yet-observable** - Score deferred. Mark interim signal and projected completion date.

**not-yet-fully-observable** - A committed or compliance KR with partial coverage. Do NOT promote a sub-signal to a KR-level pass.

Example: Committed to audit 3 healthcare accounts, 1 complete = `not-yet-fully-observable`, not "pass on in-scope"

### 5. Assess Evidence Quality

For each KR, note:
- Reliability of measurement
- Any mid-cycle target shifts
- Sample size limitations
- Measurement window mismatches

### 6. Review Initiatives as Bets

For each initiative:
- Which KR was it expected to move?
- Did it ship?
- What was its apparent contribution?
- Continue, retire, or rework?

**Ship-status is separate from KR-impact.** An initiative that shipped on time but didn't move its KR is NOT a partial win.

### 7. Synthesize Learning

Capture:
- Validated assumptions
- Invalidated assumptions
- Surprises
- Decision implications

Distinguish:
- Customer/product learnings → carry forward
- Team process learnings → hand to retrospective
- Measurement learnings → hand to instrumentation

### 8. Next-Cycle Recommendations

For each objective: continue, revise, retire, or escalate.

Suggest candidate next-cycle OKRs. Hand off to `/okr-writer`.

## Refusal Rules

The skill REFUSES these patterns:

**Retroactive Target Adjustment**
> "We hit it because we changed the target"

If changed mid-cycle, grade against BOTH the original and adjusted versions.

**Retroactive Scope Shrinkage on Committed KRs**
> "We committed to 3 accounts, 1 is done, we pass on in-scope"

Mark as `not-yet-fully-observable`. The partial result is a sub-signal, not the KR score.

**Average-the-Guardrail-Away**
> "Guardrail failed but primary was 0.9, so 0.8 average is fine"

Guardrails are separate signals. Never average.

**Aspirational-Grading-of-Committed**
> "We almost hit the contractual deadline, 0.7 is good"

Committed means 1.0 or miss. No softening.

**Effort-Equals-Impact**
> "Initiative shipped on time, KR didn't move, but still partial win"

Ship-status ≠ KR-impact. Separate them.

**Compensation Coupling**
> "Let's use OKR scores for performance reviews"

Refuse and explain sandbagging + learning-suppression risks.

## Output Format

```markdown
# OKR Cycle Review: [Team/Product] [Cycle]

## Summary
[One paragraph overall assessment]

## Scorecard

### Objective: [Title]

| KR | Type | Target | Actual | Score | Confidence |
|----|------|--------|--------|-------|------------|
| KR1 | aspirational | 50% | 42% | 0.65 | high |
| KR2 | committed | 3 accounts | 3 accounts | PASS | high |
| KR3 (guardrail) | committed | <5% churn | 4.2% | PASS | medium |

**Objective Score:** [qualitative read, not naive average]
**Guardrail Status:** [separate signal]

### Evidence Quality
- KR1: [reliable, no caveats]
- KR2: [partial coverage, see special states]
- KR3: [sample size concern for next cycle]

## Initiative Review

| Initiative | Shipped | Expected to Move | Actual Impact | Verdict |
|------------|---------|------------------|---------------|---------|
| New onboarding | ✓ | KR1 | +8pp retention | Continue |
| Email campaign | ✓ | KR1 | No visible impact | Retire |

## Learnings

**Validated:**
- [assumption that proved true]

**Invalidated:**
- [assumption that proved false]

**Surprises:**
- [unexpected finding]

## Next-Cycle Recommendations

| Objective | Recommendation | Rationale |
|-----------|----------------|-----------|
| [Title] | Continue | KRs moving, momentum |
| [Title] | Revise | Need different approach |

**Candidate OKRs for next cycle:**
- ...

**Hand-offs:**
- Measurement gaps → `/instrumentation-spec`
- Team process → `/retrospective`
- Assumption tests → `/hypothesis`

---
*Source of truth: [link to actual OKR tracker]*
```
