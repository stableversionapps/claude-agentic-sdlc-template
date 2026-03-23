---
name: user-research
description: Evaluates features and UX against user archetypes — Fast Executors, Thoughtful Planners, Beginners, and Power Users. Validates cognitive load, convenience, and the UX story arc.
---

# User Research

Validates features and UX against user archetypes and usability frameworks.

## Usage
`/user-research <feature>` — Evaluate feature against all archetypes
`/user-research journey <flow>` — Map user journey
`/user-research friction` — Identify friction points

## Archetypes

### A1: Fast Executors (Speed-First)
- Frequent users, log actions daily
- Want: speed, minimal confirmations, gestures
- Key metric: time to complete action (< 5 seconds)

### A2: Thoughtful Planners (Context-First)
- Periodic reviewers, set goals, analyze trends
- Want: context, comparisons, visual summaries

### A3: Beginners (Safety-First)
- First time with this type of app, uncertain
- Want: smart defaults, undo everywhere, low friction

### A4: Power Users (Control-First)
- Custom workflows, batch operations, automation
- Want: advanced features, customization, efficiency

## Evaluation Frameworks

### Cognitive Load Budget (max 8 per screen)
| Element | Cost |
|---------|------|
| Primary question | 0 (free) |
| Each additional action | +1 |
| Each text block to read | +1 |
| Each decision to make | +2 |
| Each unfamiliar concept | +3 |
| Each navigation choice | +1 |

### Convenience Score
- Time to complete: < 5 seconds
- Learning curve: zero for basic use
- Error recovery: 1-action undo
- Discoverability: obvious without tutorial
- Predictability: consistent patterns

### Timeless UI Tests
1. Strip test (hierarchy works without color?)
2. Trend test (still looks good in 3 years?)
3. Platform test (respects native conventions?)
4. Simplicity test (can't remove more?)
5. Sophistication test (details feel deliberate?)

## Principles
1. **5-Second Rule** — Common actions < 5 seconds
2. **Progressive Disclosure** — Simple by default
3. **Recognition > Recall** — Suggest, don't make them remember
4. **Forgiving** — Undo everywhere, edit anything
5. **Emotionally Aware** — Calm, encouraging, celebrate milestones
