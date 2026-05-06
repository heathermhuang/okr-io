# okr.io Skills

Open source AI agent skills for OKR-driven product development. Companion skills for [okr.io](https://okr.io).

## Skills

| Skill | Description | Command |
|-------|-------------|---------|
| **okr-writer** | Draft, review, and rewrite outcome-based OKRs with anti-pattern detection | `/okr-writer` |
| **okr-grader** | Score completed OKRs with type-aware interpretation and learning synthesis | `/okr-grader` |
| **office-hours** | 10-minute strategy interview that forces specificity before OKR creation | `/office-hours` |
| **weekly-checkin** | Monday commits + Friday celebrations cadence | `/weekly-checkin` |

## Installation

```bash
npx skills add heathermhuang/okr-io
```

Or clone directly:

```bash
git clone https://github.com/heathermhuang/okr-io.git
```

## Key Concepts

### OKR Type Taxonomy

Every KR has a type that determines how it's scored:

- **committed** - pass/fail against target. 1.0 is the only pass
- **aspirational** - classic OKR. 0.6-0.7 sweet spot
- **learning** - validated/invalidated. no numeric score
- **operational_health** - pass/fail/drift against threshold band
- **compliance_or_safety** - binary. met or not met

### Anti-Pattern Detection

The skills detect and warn against:

- Key Results as Tasks ("Ship X" instead of "Increase Y")
- Too Many OKRs (more than 3 objectives)
- Missing Baselines
- Sandbagged Targets
- Cascading Theater
- No Weekly Cadence

### Empowered Team Diagnostic

Asks three questions to determine if the team is truly empowered:

1. Are features/dates already committed for this cycle?
2. Can the team change initiatives mid-cycle if KRs aren't moving?
3. Who decides what gets built?

Adjusts framing for feature-teams vs empowered teams.

## Integration with okr.io

These skills are designed to work with [okr.io](https://okr.io) via MCP:

```json
{
  "mcpServers": {
    "okr-io": {
      "url": "https://okr.io/mcp"
    }
  }
}
```

## License

Apache 2.0
