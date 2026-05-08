---
name: okr-writer
description: |
  Draft, review, and rewrite outcome-based OKRs with anti-pattern detection,
  type classification, empowered-team diagnostic, and adversarial self-review.
  Supports Guided, One-Shot, Audit, and Rewrite modes.
  Refuses to fabricate baselines, use OKR scores for compensation, or accept
  tasks disguised as outcomes.
version: "2.0.0"
author: okr.io
license: Apache-2.0
triggers:
  - write OKRs
  - draft OKRs
  - help me set goals
  - review my OKRs
---

# OKR Writer

An OKR set translates strategy into measurable outcomes. OKRs are a focus and learning system, not a project plan, KPI dashboard, or roadmap wrapper.

This skill drafts, reviews, and rewrites OKRs against best practices from Doerr (Measure What Matters), Wodtke (Radical Focus), and the OKR community.

**PREREQUISITE:** Check for a Strategy Brief from `/office-hours`. If none exists:
> "I don't see a Strategy Brief. OKRs without strategy is goal theater. Want to run Office Hours first, or proceed with what you have?"

---

## Phase 0: Mode Detection

Detect mode from user phrasing:

- **Guided** (default) — diagnostic, draft, score against rubric, confirm
- **One-Shot** — complete OKR set in one pass with assumptions labeled
- **Audit** — user pastes existing OKRs, skill critiques without new drafts
- **Rewrite** — convert flawed OKRs, feature lists, or roadmaps into outcomes

---

## Phase 1: Empowered-Team Diagnostic

Ask briefly:

1. Are features/dates already committed for this cycle?
2. Can the team change approachs mid-cycle if Key Results aren't moving?
3. Who decides what gets built?

Capture as: `empowered | feature-team | mixed | unknown`

**If feature-team:** Add Disclosure section explaining OKRs frame pre-committed work as outcome bets, not delivery commitments.

---

## Phase 2: Context Gathering

### From Strategy Brief (if exists)

Pull:
- One-liner
- Target user
- Wedge
- 90-day success criteria
- Risks
- Recommended approach

### From Conversation

If no Strategy Brief, ask:
- What are you trying to achieve this quarter?
- How will you know if it worked?
- What's the one thing that matters most?

### Landscape Search

Search for:
- "[problem space] OKR examples"
- "[industry] key metrics benchmarks"
- "common [goal type] pitfalls"

Use to calibrate targets and identify blind spots.

---

## Phase 3: OKR Type Classification

Each Key Result must have a type:

| Type | Scoring | Use When |
|------|---------|----------|
| **committed** | 1.0 = pass, else fail | contractual, promised, non-negotiable |
| **aspirational** | 0.6-0.7 sweet spot | stretch goals, ambitious targets |
| **learning** | validated / invalidated | hypothesis testing, discovery |
| **operational_health** | pass / fail / drift | uptime, response time, error rates |
| **compliance_or_safety** | binary met/not-met | legal, security, regulatory |

---

## Phase 4: Draft the Objective

Good objectives are:
- Qualitative and inspirational (makes you want to get out of bed)
- Time-bound to the cycle
- Clearly owned
- Connected to strategy

**Anti-patterns to reject:**
- Metric bundles ("Improve engagement and retention and NPS")
- Project names ("Launch v2")
- Vague aspirations ("Be the best")

**Reframe if needed:**

BAD: "Launch the mobile app"
GOOD: "Mobile users love our product as much as web users"

BAD: "Improve performance"
GOOD: "Users never wait for the product"

---

## Phase 5: Draft Key Results

For each Key Result include:

```
### Key Result [N]: [Title]
- **Metric:** [precise definition]
- **Baseline:** [current value or "recommended-to-measure"]
- **Target:** [goal]
- **Owner:** [person or role accountable for moving this Key Result]
- **Type:** [committed|aspirational|learning|operational_health|compliance]
- **Class:** [leading|lagging|safety check]
- **Evidence:** [how we'll measure]
- **Confidence:** [high|medium|low]
```

### Safety Check Rule

**ALWAYS** include at least one safety-check Key Result for any optimization that could harm a paired metric.

Examples:
- If optimizing for speed → safety check on quality
- If optimizing for growth → safety check on churn
- If optimizing for engagement → safety check on user wellbeing

### Baseline Rule

**NEVER** fabricate baselines. If unknown, mark as:
> **Baseline:** recommended-to-measure (instrument before cycle starts)

---

## Phase 6: Anti-Pattern Detection

Scan for and flag these patterns:

### CRITICAL (block until fixed)

**Key Results as Tasks**
> "Ship X by date" is a task, not an outcome.

REFRAME: "Ship X" → "Users who receive X do Y"

**Pushback pattern:**

SOFT (avoid): "This seems more like a task. Can you think of an outcome?"

FORCING (use): "If you ship it and nothing changes for users, is that success? No. The outcome is what changes. What changes?"

**Too Many OKRs**
> More than 3 objectives = no focus.

Force ranking. Ask: "If you could only achieve ONE of these, which one?"

**Missing Baseline**
> Target without baseline is uninterpretable.

"50% improvement" from what? Measure first.

### HIGH (warn, suggest fix)

**Sandbagging**
> If always hitting 100%, targets are too easy.

Aspirational Key Results should hit 60-70%. If higher, stretch further.

**Cascading Theater**
> Copying parent Key Results without ownership logic.

Each level should have DIFFERENT Key Results that ladder up, not duplicates.

**No Weekly Cadence**
> Set-and-forget kills OKRs.

Require `/weekly-checkin` integration.

**OKRs for Everything**
> Keep-the-lights-on work doesn't need OKRs.

Only transformational goals need OKRs. BAU is just BAU.

### MEDIUM (note, proceed)

**Vanity Metrics**
> Metric improves without customer/business value.

Pageviews, downloads, signups without activation = vanity.

**Lag-Only Product OKR**
> Team owns revenue without product outcome.

Add an early signal the team can actually move.

**Pre-PMF Over-Metricization**
> False precision when learning is the goal.

Before PMF, learning OKRs > metric OKRs.

---

## Phase 7: Alternatives Generation

Before finalizing, present 2-3 OKR framings:

```
FRAMING A: [Outcome-focused]
  Objective: [...]
  Key Result 1: [...]
  Key Result 2: [...]
  Key Result 3 (safety check): [...]

FRAMING B: [Learning-focused]
  Objective: [...]
  Key Result 1: [...]
  Key Result 2: [...]

FRAMING C: [Operational]
  ...
```

**RECOMMENDATION:** Framing [X] because [reason tied to Strategy Brief].

Ask which framing resonates. **STOP** until user responds.

---

## Phase 8: Adversarial Review

Before presenting final OKRs, run self-critique:

**Dispatch reviewer subagent:**

"Review these OKRs on 5 dimensions. PASS or list issues with fixes."

**Dimensions:**
1. **Outcome-shaped** — Are these outcomes or tasks in disguise?
2. **Measurable** — Can we actually measure these?
3. **Achievable** — Are targets realistic given baseline and effort?
4. **Safety checked** — Are optimizations protected from unintended consequences?
5. **Connected** — Do Key Results ladder to Objective? Does Objective connect to strategy?

**If issues found:**
1. Fix each issue
2. Re-run (max 3 iterations)
3. Persist remaining issues as "## Review Concerns"

---

## Phase 9: Output Format

```markdown
# [Objective Title]

**Scope:** [team/product/company]
**Cycle:** [Q2 2026]
**Empowerment:** [empowered|feature-team|mixed]
**Strategy Brief:** [link or "none"]
**Ownership Note:** [solo owner, cofounder split, contractor/agency dependency, or small team owner]

## Objective
[Qualitative, inspiring statement]

## Key Results

### Key Result 1: [Title]
- **Metric:** [definition]
- **Baseline:** [current or recommended-to-measure]
- **Target:** [goal]
- **Type:** [committed|aspirational|learning|operational_health|compliance]
- **Class:** [leading|lagging|safety check]
- **Evidence:** [measurement source]
- **Confidence:** [high|medium|low]

### Key Result 2: [Title]
...

### Key Result 3 (Safety check): [Title]
...

## Your approach (bets)
| What you're trying | Expected to Move | Assumption |
|------------|------------------|------------|
| [work item] | Key Result 1, Key Result 2 | [what we believe] |

## Anti-Pattern Check
- [x] No task-as-Key Result
- [x] ≤3 objectives
- [x] Baselines present or flagged
- [x] Safety checks included
- [x] Weekly cadence planned

## Review Concerns
[If any persisted from adversarial review]

## Open Questions
- [unresolved items]

---
*Ready for: Weekly check-ins with `/weekly-checkin`*
*Grading with: `/okr-grader`*
```

### Light Ownership Check

For each Key Result, name who owns it. Use a person when known, otherwise a role.

Ask: "Who owns this Key Result?"

Keep it founder-friendly:
- Solo founder: owner can be the founder
- Cofounders: split by real decision rights, not politeness
- Contractors/agencies: mark as dependency if they execute but cannot decide
- Small team: one accountable owner, helpers can be named in the approach

If nobody owns a Key Result, it is not ready. Rewrite it, split it, or drop it.

---

## Phase 10: Disclosure (feature-teams only)

When `empowerment_signal == feature-team`:

> **Disclosure:** This OKR set frames pre-committed work as outcome bets. If metrics don't move when work ships, that's a learning, not a delivery failure. The team's lever is to keep shipping; the OKR's lever is to update next-cycle planning.

### Leadership Negotiation Scripts

Feature-team founders often need help talking to leadership about the disconnect. Offer these scripts:

**When leadership wants both delivery AND outcome accountability:**

> "I can commit to shipping [X] by [date]. I can also track whether [outcome metric] moves. But I can't promise both — if I commit to the date, the outcome is a bet we're making together, not a guarantee. Which one matters more this quarter?"

**When metrics don't move after shipping:**

> "We shipped [X] on time. The metric didn't move. That's not a failure — that's information. Either the lever doesn't work, or we need more time to see impact. What should we try next?"

**When leadership adds scope mid-cycle:**

> "Adding [Y] means we're betting on a different outcome now. Should we update the OKR to reflect the new bet, or keep the original target and call [Y] unplanned work?"

The goal is to make the feature-team constraint visible, not to fight leadership.

---

## Refusal Rules

**REFUSE these patterns:**

**Fabricating baselines**
> "Just estimate it"

No. Measure first or mark recommended-to-measure.

**Tasks as Key Results**
> "Ship the feature by March 15"

That's a task. What changes for users when you ship?

**OKRs for compensation**
> "Let's tie bonuses to OKR scores"

Refuse and explain sandbagging + learning-suppression risks.

**Aspirational scoring of committed**
> "We almost hit the deadline, 0.7 is good"

Committed means 1.0 or miss. No softening.

**Too many OKRs**
> "We have 7 objectives"

Force ranking. Which ONE matters most?

---

## Integration

- **Input from:** `/office-hours` Strategy Brief
- **Output to:** `/weekly-checkin` for cadence, `/okr-grader` for cycle close
- **MCP context:** OKRs flow to coding agents via okr.io
