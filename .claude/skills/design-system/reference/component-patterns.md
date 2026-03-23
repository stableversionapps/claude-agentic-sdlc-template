# Component Patterns Reference

## Theme Usage

Always use the theme system for colors and text styles. Never hardcode values.

```
// Pseudocode — adapt to your framework
color = theme.colorScheme.primary
textStyle = theme.textTheme.bodyLarge
```

## Card Component Pattern

```
Card {
  padding: designSystem.cardPadding (20px)
  radius: designSystem.cardRadius (20px)
  background: theme.colorScheme.surface
  shadow: light mode only (subtle blur), dark mode uses surface elevation
  border: NONE — use spacing and surface color for grouping
}
```

## Shadow System

### Light Mode
- Cards: `0 2px 8px rgba(0,0,0,0.04)` — barely visible, just enough depth
- Modals: `0 -4px 24px rgba(0,0,0,0.12)` — slightly more prominent
- FAB: `0 4px 16px rgba(0,0,0,0.15)` — floating elements

### Dark Mode
- NO shadows — use surface color steps for elevation
- Level 0: background color
- Level 1: surface color
- Level 2: elevated surface color
- Level 3: highest surface color

## Amount / Number Display Pattern

```
AmountDisplay {
  value: formatted number
  style: theme.textTheme.displayLarge (hero) or bodyLarge (inline)
  color: contextual — success for positive, error for negative, default for neutral
  semantic label: "Amount: [formatted value]" for screen readers
}
```

## Loading Shimmer Pattern

- Use skeleton shimmer for ALL loading states
- NEVER use spinners for content areas
- Shimmer shape matches the content it replaces
- Subtle animation: 1-2s loop, respect reduced-motion

## Empty State Pattern

```
EmptyState {
  illustration: relevant, encouraging (not a sad face)
  title: "No [items] yet"
  subtitle: "Tap [action] to get started"
  action: primary button to create first item
}
```

## Error State Pattern

```
ErrorState {
  icon: warning/error icon
  title: "Something went wrong"
  subtitle: specific, helpful error message
  action: "Try Again" button that retries the operation
}
```

## Spacing Rules

- Use the 8pt grid: 4, 8, 16, 24, 32, 48
- Spacing is the PRIMARY layout tool
- NO borders or dividers unless functionally necessary
- Group related items with tighter spacing
- Separate sections with larger spacing
