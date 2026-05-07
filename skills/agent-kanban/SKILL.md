---
name: agent-kanban
description: |
  Track what your AI coding agents are doing with a local kanban board.
  Generates a visual HTML file showing tasks in progress, blocked items,
  and completed work. No server, no signup. Local-first coordination.
version: "2.0.0"
author: okr.io
license: Apache-2.0
triggers:
  - update kanban
  - what are agents doing
  - task status
  - show board
---

# Agent Kanban

Track what your AI coding agents are doing with a local kanban board.

---

## What It Does

Generates a `.kanban.html` file in your project root showing:
- What tasks are in progress
- Which agent is working on each
- What's blocked and why
- Recently completed work
- Time spent per task

No server, no signup. Just a local file you can open in any browser.

---

## When to Use

Call this skill when you:
- **Start a task** → add to "Doing"
- **Complete a task** → move to "Done"
- **Hit a blocker** → move to "Blocked" with note
- **Need status** → regenerate board

---

## Commands

### Start a Task

```
Update kanban: starting [task description]
Agent: [your role, e.g. "Backend", "Frontend", "Research"]
KR: [optional - which KR this moves]
```

### Complete a Task

```
Update kanban: completed [task description]
Output: [brief summary of deliverable]
Duration: [optional - how long it took]
```

### Block a Task

```
Update kanban: blocked [task description]
Reason: [what's blocking]
Need: [what input is required from human]
```

### Unblock a Task

```
Update kanban: unblocked [task description]
Resolution: [how it was resolved]
```

### Regenerate Board

```
Update kanban: refresh
```

---

## State File

The skill maintains `.kanban-state.json` with task history:

```json
{
  "tasks": [
    {
      "id": "abc123",
      "title": "Write landing page hero copy",
      "status": "done",
      "agent": "Writer",
      "kr": "KR1: Conversion 2%→5%",
      "started": "2026-05-06T10:30:00Z",
      "completed": "2026-05-06T10:45:00Z",
      "duration_minutes": 15,
      "output": "Hero copy in src/components/Hero.tsx"
    },
    {
      "id": "def456",
      "title": "Add payment integration",
      "status": "blocked",
      "agent": "Backend",
      "kr": "KR2: Revenue $0→$1k",
      "started": "2026-05-06T11:00:00Z",
      "blocked_at": "2026-05-06T11:30:00Z",
      "blocked_reason": "Need Stripe API key",
      "blocked_need": "Human to add STRIPE_SECRET_KEY to .env"
    }
  ],
  "agents": [
    {"name": "Backend", "color": "#4CAF50"},
    {"name": "Frontend", "color": "#2196F3"},
    {"name": "Writer", "color": "#9C27B0"},
    {"name": "Research", "color": "#FF9800"}
  ]
}
```

---

## HTML Board

The generated `.kanban.html` includes:

### Visual Design
- Dark theme, clean UI
- Three columns: Doing, Blocked, Done (recent 10)
- Color-coded by agent
- Time elapsed for in-progress tasks
- Duration for completed tasks

### Card Contents
- Task title
- Agent name + color
- KR tag (if linked)
- Timestamp
- Notes/output
- Blocked reason (if blocked)

### Interactivity
- Auto-refreshes every 30 seconds (if open)
- Click card to expand details
- Filter by agent or KR
- Search tasks

---

## Integration with OKRs

Link tasks to KRs for visibility:

```
Update kanban: starting "Implement retry logic for API calls"
Agent: Backend
KR: KR3: Uptime 99%→99.9%
```

The board shows which KRs have active work vs which are stalled.

---

## Multi-Agent Coordination

When multiple agents work in parallel:

### Claim Protocol
Before starting a task, check if already claimed:
```
Update kanban: check [task description]
```

If unclaimed, claim it:
```
Update kanban: starting [task description]
Agent: [role]
```

### Handoff Protocol
When passing work to another agent:
```
Update kanban: handoff [task description]
From: [current agent]
To: [next agent]
Context: [what the next agent needs to know]
```

### Conflict Detection
The board highlights if two agents claim the same task.

---

## CLAUDE.md Integration

Add to your project's CLAUDE.md or AGENTS.md:

```markdown
## Workflow Tracking

Use the agent-kanban skill to track work:
- When starting a task: update kanban with what you're doing
- When completing: update kanban with the result
- When blocked: update kanban with what you need
- Link tasks to KRs when relevant

The human can open .kanban.html anytime to see progress.
```

---

## Example Flow

Agent starts:
```
Update kanban: starting "Write landing page hero copy"
Agent: Writer
KR: KR1: Conversion 2%→5%
```

Agent completes:
```
Update kanban: completed "Write landing page hero copy"
Output: Hero in src/components/Hero.tsx — "Ship faster with AI"
Duration: 15 minutes
```

Another agent hits blocker:
```
Update kanban: blocked "Add payment integration"
Reason: Need Stripe API key from human
Need: Add STRIPE_SECRET_KEY to .env
```

Human opens `.kanban.html`:
- Sees Writer finished hero (15 min)
- Sees Backend blocked on Stripe key
- Adds the key, notifies Backend

Backend continues:
```
Update kanban: unblocked "Add payment integration"
Resolution: Human added Stripe key
```

---

## Metrics

The board calculates:

- **Throughput:** Tasks completed per day
- **Cycle time:** Average time from start to done
- **Block rate:** % of tasks that hit blockers
- **Agent utilization:** Time spent working vs blocked

Surfaces in weekly check-ins via `/weekly-checkin`.

---

## Why Local-First

- Works offline
- No signup or API keys
- No data leaves your machine
- Portable across projects
- Version controllable (commit .kanban-state.json for history)
- Opens in any browser
- No dependencies

---

## Cleanup

Periodically clean old tasks:

```
Update kanban: archive completed before [date]
```

Moves old completed tasks to `.kanban-archive.json`.
