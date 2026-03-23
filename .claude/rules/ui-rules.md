---
paths:
  - "src/**/components/**/*"
  - "src/**/pages/**/*"
  - "src/**/screens/**/*"
  - "src/**/views/**/*"
  - "lib/**/presentation/**/*"
  - "lib/**/widgets/**/*"
  - "app/**/ui/**/*"
---

# Zero-Noise UI Rules

<!-- Customize paths above for your project structure -->

## Screen Design
- Every screen answers only 1 primary question
- Maximum 3 primary actions per screen
- Screen rhythm: Entry Focus -> Action Zone -> Exit Clarity
- Use spacing for layout structure — no borders or dividers unless functionally required

## Component States (ALL 5 required for every data-driven component)
1. Default — normal presentation
2. Loading — skeleton shimmer (NEVER spinner for content)
3. Empty — helpful illustration + action prompt
4. Error — clear message + retry action
5. Success — subtle confirmation

## Motion
- Motion = meaning. No decorative animation.
- Fast: 100-150ms | Normal: 200-300ms | Emphasis: 400ms
- Always respect reduced-motion system settings

## Theming
- All colors via theme system
- All text styles via theme typography
- All dimensions via design system constants
- Both light and dark mode must work
- Dark mode: surface color elevation, NO shadows

## Accessibility
- Touch/click targets >= 44dp with adequate spacing
- Semantic labels on all icons and images
- Color never sole information carrier
