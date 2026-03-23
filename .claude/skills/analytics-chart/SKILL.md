---
name: analytics-chart
description: Creates data visualizations following zero-noise design. One hero chart per view, tap/click to drill down, table alternative for accessibility. Use for any analytics or dashboard chart.
---

# Analytics Chart Skill

Builds premium data visualizations following zero-noise design principles.

> One hero chart at a time. Tap/click to drill down. Never compete for attention.

## Chart Design Principles

### Zero-Noise Charts
- **One chart per viewport** — never two competing visualizations
- Tap/click to drill down for details
- Minimal grid lines (barely visible)
- Axis labels in caption style (small, subdued)
- No chart titles that repeat what the section header says
- Animate only on initial load and data change (functional, not decorative)

### Accessibility
- Every chart MUST have a text/table alternative for screen readers
- Announce summary for screen readers
- Interactive elements have semantic labels
- Color not sole indicator — use patterns/labels alongside colors

## Chart Types

### 1. Trend Chart (Line/Bar)
- Time-series data over time
- Previous period comparison: dashed line (subtle, not competing)
- Hero number above chart: total for period
- Touch/click: show value tooltip

### 2. Category Breakdown (Donut/Pie)
- Top 5-7 categories + "Other" grouping
- Color-coded with category palette
- Center text: total (the hero number)
- Tap segment -> drill-down detail view
- Legend below chart, not beside (mobile-friendly)

### 3. Progress Bar (Horizontal)
- Spent/used vs total as a progress bar
- Color transitions: green -> yellow (75%) -> red (100%+)
- Text: "X of Y" and time/quantity remaining

### 4. Area/Stacked Chart
- Multi-series data as stacked areas
- Primary metric line on top
- Period toggles: simple pill selector
- Hero number: current value, prominent

### 5. Waterfall Chart
- Flow from start to end with positive/negative steps
- Green (positive) / Red (negative) bars
- Running total line
- Simple, scannable at a glance

## Design Requirements
- Use theme system for ALL colors
- Grid: barely visible (use outline/muted color)
- Labels: small caption style
- Smooth animations (respect reduced-motion)
- Touch/click: tooltip on interaction, drill-down on full tap
- All 5 states: loading shimmer, empty ("No data yet"), error, data, success
