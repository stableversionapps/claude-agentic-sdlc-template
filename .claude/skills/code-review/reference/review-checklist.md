# Code Review Checklist

## Architecture
- [ ] Feature-first folder structure
- [ ] Clean architecture layers (presentation | domain | data)
- [ ] No layer violations (presentation never imports data directly)
- [ ] Repository pattern with abstract interfaces
- [ ] Single-responsibility use cases
- [ ] Domain entities are immutable

## Zero-Noise UI
- [ ] Each screen answers only 1 primary question
- [ ] Max 3 primary actions per screen
- [ ] Spacing for structure (no borders/dividers unless functional)
- [ ] No decorative elements without purpose
- [ ] No competing CTAs in same viewport
- [ ] Progressive disclosure for complexity
- [ ] Screen rhythm: Entry Focus -> Action Zone -> Exit Clarity

## Component States (ALL 5)
- [ ] Default state
- [ ] Loading state (skeleton shimmer, never spinner for content)
- [ ] Empty state (helpful + actionable)
- [ ] Error state (clear message + retry)
- [ ] Success state (subtle confirmation)

## Code Quality
- [ ] No unused imports or dead code
- [ ] Proper null safety
- [ ] Proper error handling (no swallowed exceptions)
- [ ] No hardcoded strings
- [ ] No hardcoded colors/sizes (use theme system)
- [ ] Resources properly disposed/cleaned up
- [ ] Immutable constructors where possible
- [ ] No logic in view/build methods

## Security
- [ ] No hardcoded secrets (API keys, tokens, passwords)
- [ ] No sensitive data in logs or error messages
- [ ] Input validation/sanitization
- [ ] Sensitive data encrypted at rest

## Performance
- [ ] No unnecessary re-renders
- [ ] Virtualized/lazy lists for large datasets
- [ ] DB queries indexed
- [ ] No blocking operations on main thread
- [ ] Images cached and properly sized

## Accessibility
- [ ] Touch/click targets >= 44dp
- [ ] Semantic labels on icons/images
- [ ] Color not sole information carrier
- [ ] Works at 200% text scale
- [ ] Reduced-motion respected

## Tests
- [ ] 80%+ coverage on changed code
- [ ] All tests passing
- [ ] Edge cases covered
- [ ] Both themes tested (if UI)
