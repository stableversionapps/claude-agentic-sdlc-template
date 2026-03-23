---
name: create-widget
description: Creates reusable components following zero-noise design. Spacing over borders, all 5 states, functional motion only, proper theming, and accessibility. Use when building shared UI components.
argument-hint: "component-name"
---

# Create Component Skill

Builds reusable, themeable UI components following zero-noise design principles.

## Component Hierarchy

### Level 1: Primitives
- Button, Text, Icon, Spacer
- Theming at this level — never hardcoded values

### Level 2: Composites
- Card, ListItem, InputField, Badge
- Combine primitives with design system tokens

### Level 3: Patterns
- Domain-specific cards, progress indicators, insight displays
- Business logic integration, all 5 states

## Checklist

### Zero-Noise
- [ ] No borders — use spacing and surface color for grouping
- [ ] No decorative elements without function
- [ ] Spacing from design system (xs/sm/md/lg/xl/xxl)
- [ ] Primary color used sparingly (accent, not fill)

### Theming
- [ ] Theme system for all colors and text styles
- [ ] Works in light AND dark mode
- [ ] Dark mode: surface elevation instead of shadows
- [ ] Immutable constructor

### States (ALL 5 for data-driven components)
- [ ] Default — normal presentation
- [ ] Loading — skeleton shimmer
- [ ] Empty — helpful prompt
- [ ] Error — message + retry
- [ ] Success — subtle feedback

### Motion
- [ ] Functional motion only
- [ ] Respects reduced-motion system setting
- [ ] Fast: 100-150ms | Normal: 200-300ms | Emphasis: 400ms

### Accessibility
- [ ] Touch/click targets >= 44dp
- [ ] Semantic labels for screen reader
- [ ] Color not sole information carrier
- [ ] Adequate spacing between interactive elements

### Quality
- [ ] Accepts customization via parameters/props
- [ ] Tests created
- [ ] Works at 200% text scale
