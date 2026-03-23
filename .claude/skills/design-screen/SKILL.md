---
name: design-screen
description: Designs and builds screens following the zero-noise design philosophy. Every screen answers 1 question, has max 3 actions, uses spacing over borders, supports all 5 component states, and works in both themes. Use when creating any screen or page.
argument-hint: "screen-name"
---

# Design Screen Skill

Builds production-quality screens following zero-noise design philosophy.

> "The best UI is not minimal — it is *inevitable*."

## Steps

1. Read the screen requirements from the project requirements document
2. Identify: What is the **1 primary question** this screen answers?
3. Identify: What are the **max 3 primary actions**?
4. Read design tokens from the design system
5. Build the component tree following screen rhythm

## Screen Rhythm (EVERY Screen)

```
Entry Focus -> Action Zone -> Exit Clarity
```

1. **Entry Focus** — User understands the screen in < 1 second
2. **Action Zone** — Clear, limited actions (max 3 primary)
3. **Exit Clarity** — Obvious where to go next

## Mandatory Checks

### Zero-Noise Compliance
- [ ] Screen answers only 1 primary question
- [ ] Max 3 primary actions
- [ ] Spacing used for structure — no borders/dividers
- [ ] No decorative elements without function
- [ ] No competing CTAs in the same viewport
- [ ] Progressive disclosure for complexity

### Theming
- [ ] Uses theme system — no hardcoded colors or text styles
- [ ] Works in both light and dark mode
- [ ] Uses design system spacing constants
- [ ] Consistent radius values for cards, buttons, modals

### Component States (ALL 5)
- [ ] Default — normal presentation
- [ ] Loading — skeleton shimmer (not spinner)
- [ ] Empty — encouraging illustration + action
- [ ] Error — clear message + retry
- [ ] Success — subtle confirmation

### Motion
- [ ] Functional motion only (no decorative animation)
- [ ] Respects reduced-motion system setting
- [ ] Timing: 100-150ms fast | 200-300ms normal | 400ms emphasis

### Accessibility
- [ ] Touch/click targets >= 44dp with adequate spacing
- [ ] Semantic labels on all icons/images
- [ ] Color not sole information carrier

### Responsive
- [ ] Adapts to different screen/window sizes
- [ ] Content readable at 200% text scale
- [ ] Primary actions in easily accessible zones

## Flow Pattern
```
Overview -> Drill Down -> Action -> Feedback -> Return
```
No dead ends. No over-nested navigation. No modal overuse.
