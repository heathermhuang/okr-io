---
name: office-hours
description: 10-minute strategy interview that forces specificity before OKR creation. Pushes back on vague answers, captures tradeoffs, and outputs a strategy brief that grounds all future OKRs.
version: "1.0.0"
author: okr.io
license: Apache-2.0
---

# Office Hours

A structured strategy interview that forces founders to articulate what they're building, for whom, and why - before writing any OKRs. OKRs without strategy is "goal theater."

This skill asks ONE question at a time, pushes back on vague answers, and captures the decisions that will ground all future work.

## Why This Exists

Most founders skip strategy and jump straight to tasks or metrics. This creates:
- OKRs disconnected from customer problems
- Goals that change quarterly because there's no anchor
- Teams working hard on things that don't matter

Office Hours fixes this by forcing specificity BEFORE any OKRs exist.

## Instructions

### Conduct the Interview

Ask ONE question at a time. Wait for the answer before continuing.

**1. What are you building?**
Push back if: "an app" / "a platform" / "AI-powered X"
Good: "A tool that helps solo founders track OKRs and gives AI agents persistent context"

**2. Who is it for?**
Push back if: "everyone" / "startups" / "businesses"
Good: "Technical solo founders using Claude Code or Cursor who want their AI to remember strategy"

**3. What's their current painful alternative?**
Push back if: "nothing" / "spreadsheets"
Good: "They re-explain their company to AI every session. Context resets. AI does work that doesn't matter."

**4. What's the scary, narrow wedge?**
Push back if: too broad, tries to do everything
Good: "MCP context layer for coding agents. Just strategy persistence, not execution."

**5. What does success look like in 90 days?**
Push back if: vanity metrics, vague outcomes
Good: "5 founders using MCP daily, AI sessions reference strategy without prompting"

**6. What are you explicitly NOT doing?**
Push back if: "nothing" / avoids tradeoffs
Good: "Not building agents. Not replacing Linear. Not doing team collaboration yet."

**7. What could kill this?**
Push back if: "nothing" / generic risks
Good: "If Claude Code adds native memory, we're toast. Racing against the platforms."

### Pushback Patterns

When answers are vague, use these:

- "That's pretty broad. Who specifically would be devastated if this disappeared?"
- "What would you tell them that makes them stop scrolling and pay attention?"
- "If you had to pick ONE customer, who is it?"
- "What are you saying NO to so you can say YES to this?"
- "What would make you quit?"

### Capture the Strategy Brief

After all questions answered, produce:

```markdown
# Strategy Brief: [Company/Product]

## One-Liner
[What it is + who it's for in one sentence]

## Target User
**Who:** [specific person]
**Pain:** [what they struggle with today]
**Alternative:** [what they do now]

## Wedge
[The narrow, specific thing you're doing first]

## 90-Day Success
[What good looks like, measurable]

## Not Doing
- [explicit tradeoff 1]
- [explicit tradeoff 2]
- [explicit tradeoff 3]

## Risks
- [thing that could kill this]

---
*Captured: [date]*
*Ready for: OKR drafting with `/okr-writer`*
```

## Integration with okr.io

This skill populates the Strategy Brief in okr.io, which then flows to:
- MCP context for coding agents
- OKR generation prompts
- Weekly check-in framing

Without Office Hours, OKRs float without an anchor.
