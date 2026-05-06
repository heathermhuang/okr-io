---
name: okr-writer
description: Draft, review, and rewrite outcome-based OKRs with anti-pattern detection, type classification, and empowered-team diagnostic. Supports Guided, One-Shot, Audit, and Rewrite modes. Refuses to fabricate baselines or use OKR scores for compensation.
version: "1.0.0"
author: okr.io
license: Apache-2.0
---

# OKR Writer

An OKR set translates strategy into measurable outcomes. OKRs are a focus and learning system, not a project plan, KPI dashboard, or roadmap wrapper.

This skill drafts, reviews, and rewrites OKRs against best practices from Doerr (Measure What Matters), Wodtke (Radical Focus), and the OKR community.

## Modes

Detect mode from user phrasing:

- **Guided** (default) - diagnostic, draft, score against rubric, ask to confirm
- **One-Shot** - complete OKR set in one pass with assumptions labeled
- **Audit** - user pastes existing OKRs, skill critiques without new drafts
- **Rewrite** - convert flawed OKRs, feature lists, or roadmaps into outcome-shaped OKRs

## Instructions

### 1. Run Empowered-Team Diagnostic

Ask briefly:
- Are features/dates already committed for this cycle?
- Can the team change initiatives mid-cycle if KRs aren't moving?
- Who decides what gets built?

Capture as: `empowered | feature-team | mixed | unknown`

If feature-team, add Disclosure section to output explaining OKRs frame pre-committed work as outcome bets.

### 2. Classify OKR Type

Each KR must have a type:

| Type | Scoring | Use When |
|------|---------|----------|
| **committed** | 1.0 = pass, anything else = fail | contractual, promised, non-negotiable |
| **aspirational** | 0.6-0.7 sweet spot | stretch goals, ambitious targets |
| **learning** | validated / invalidated | hypothesis testing, discovery |
| **operational_health** | pass / fail / drift-within-tolerance | uptime, response time, error rates |
| **compliance_or_safety** | binary met/not-met | legal, security, regulatory |

### 3. Separate Outcomes from Work

Move features, tasks, and milestones to Initiatives. The OKR is what changes in the world; Initiatives are bets on how to make that change.

Castro's test: "if it can go in your backlog, it is not an outcome."

### 4. Draft the Objective

Good objectives are:
- Qualitative and inspirational (makes you want to get out of bed)
- Time-bound to the cycle
- Clearly owned
- Connected to strategy

Bad objectives: metric bundles, project names, vague aspirations

### 5. Draft Key Results

For each KR include:
- Metric definition
- Baseline (or mark `recommended-to-measure` if missing)
- Target
- Evidence source
- Type (committed | aspirational | learning | operational_health | compliance_or_safety)
- Indicator class (leading | lagging | guardrail)

Always include at least one guardrail KR for any optimization that could harm a paired metric.

### 6. Anti-Pattern Detection

Scan for and flag these patterns:

**CRITICAL:**
- **Key Results as Tasks** - "Ship X by date" is a task, not an outcome. Reframe to "Increase Y from A to B"
- **Too Many OKRs** - More than 3 objectives = no focus. Force ranking.
- **Missing Baseline** - Target without baseline is uninterpretable

**HIGH:**
- **Sandbagging** - If always hitting 100%, targets are too easy
- **Cascading Theater** - Copying parent KRs without ownership logic
- **No Weekly Cadence** - Set-and-forget kills OKRs
- **OKRs for Everything** - Keep-the-lights-on work doesn't need OKRs

**MEDIUM:**
- **Vanity Metrics** - Metric improves without customer/business value
- **Lag-Only Product OKR** - Team owns revenue without product outcome
- **Pre-PMF Over-Metricization** - False precision when learning is the goal

## Constraint Rules

**MUST:**
- Measure outcomes (customer behavior, business KPI delta), not features or tasks
- Include guardrail KR for any growth/speed/volume optimization
- Default to team-level OKRs (warn if individual OKRs requested)
- Mark missing baselines explicitly

**MUST NOT:**
- Fabricate baselines, targets, or benchmarks
- Use OKR scores for compensation (refuse and explain sandbagging risk)
- Treat 0.7 as success for committed/compliance KRs (those target 1.0)

## Output Format

```markdown
# [Objective Title]

**Scope:** [team/product/company]
**Cycle:** [Q2 2026]
**Type:** [committed/aspirational/learning]
**Empowerment:** [empowered/feature-team/mixed]

## Objective
[Qualitative, inspiring objective statement]

## Key Results

### KR1: [Title]
- **Metric:** [definition]
- **Baseline:** [current value or recommended-to-measure]
- **Target:** [goal]
- **Type:** [committed/aspirational/learning/operational_health/compliance_or_safety]
- **Class:** [leading/lagging/guardrail]
- **Evidence:** [how we'll measure]
- **Confidence:** [high/medium/low]

### KR2: [Title]
...

### KR3 (Guardrail): [Title]
...

## Initiatives (Bets)
| Initiative | Expected to Move | Assumption |
|------------|------------------|------------|
| ... | KR1, KR2 | ... |

## Anti-Pattern Check
- [ ] No task-as-KR
- [ ] ≤3 objectives
- [ ] Baselines present
- [ ] Guardrails included
- [ ] Weekly cadence planned

## Open Questions
- ...

---
*Source of truth: [link to actual OKR tracker]*
```

## Disclosure (for feature-teams)

When `empowerment_signal == feature-team`:

> **Disclosure:** This OKR set frames pre-committed work as outcome bets. If the metrics do not move when the work ships, that is a learning, not a delivery failure. The team's lever this cycle is to keep shipping; the OKR's lever is to update next-cycle planning.
