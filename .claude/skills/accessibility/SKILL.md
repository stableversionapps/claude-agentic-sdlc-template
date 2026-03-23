---
name: accessibility-check
description: Audits screens for WCAG 2.1 AA compliance — contrast ratios, touch targets, screen reader support, text scaling, and semantic labels.
---

# Accessibility Check

Ensures the application meets WCAG 2.1 AA standards for all users.

## Usage
`/accessibility-check` — Full app audit
`/accessibility-check <screen>` — Audit specific screen

## Checklist

### Visual
- [ ] Contrast ratio >= 4.5:1 (normal text), >= 3:1 (large text 18sp+)
- [ ] Color not sole information carrier (icons/labels alongside colors)
- [ ] Support system font scaling to 200%
- [ ] Both themes meet contrast independently

### Motor
- [ ] All touch/click targets >= 44x44dp
- [ ] Click/tap alternatives for all gesture-based actions
- [ ] No auto-dismissing important notifications
- [ ] Adequate spacing between interactive elements (8px minimum)

### Screen Reader
- [ ] All icons/images have semantic labels
- [ ] Logical focus order matching visual layout
- [ ] Live regions for dynamic content updates
- [ ] Data visualizations provide text alternatives
- [ ] State changes announced (loading, error, success)

### Cognitive
- [ ] Domain terms explained on first use
- [ ] Consistent navigation patterns
- [ ] Clear error messages with recovery actions
- [ ] Progressive disclosure (simple defaults, reveal complexity)
- [ ] Max 3 primary actions per screen

### Animation
- [ ] Respects reduced-motion system setting
- [ ] No essential content behind animations
- [ ] Reduced motion alternatives provided
- [ ] No animation > 400ms (except page transitions)
