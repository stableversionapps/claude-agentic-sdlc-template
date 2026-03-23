---
name: design-system
description: Implements and enforces the project design system — colors, typography, spacing, shadows, components. Ensures visual consistency across all screens. Use when building or reviewing UI.
user-invocable: false
---

# Design System

Implements and enforces the design system across all UI components.

## Usage
`/design-system audit` — Audit codebase for design system violations
`/design-system component <name>` — Create a new design system component
`/design-system tokens` — Show all current design tokens

## Design Tokens

<!-- Customize for your project -->

### Colors (use via theme system, never hardcode)
| Token | Light | Dark |
|-------|-------|------|
| primary | `[YOUR_PRIMARY]` | `[YOUR_PRIMARY]` |
| secondary | `[YOUR_SECONDARY]` | `[YOUR_SECONDARY]` |
| background | `[YOUR_LIGHT_BG]` | `[YOUR_DARK_BG]` |
| surface | `[YOUR_LIGHT_SURFACE]` | `[YOUR_DARK_SURFACE]` |
| success | `#10B981` | `#10B981` |
| error | `#EF4444` | `#EF4444` |
| warning | `#F59E0B` | `#F59E0B` |

### Typography
| Style | Size | Weight | Use |
|-------|------|--------|-----|
| displayLarge | 32sp | Bold 700 | Hero numbers |
| headlineMedium | 24sp | SemiBold 600 | Section titles |
| titleMedium | 18sp | Medium 500 | Card headers |
| bodyLarge | 16sp | Regular 400 | Body text |
| bodyMedium | 14sp | Regular 400 | Secondary text |
| labelSmall | 12sp | Regular 400 | Captions |

### Dimensions
| Token | Value |
|-------|-------|
| cardRadius | 20px |
| buttonRadius | 12px |
| modalRadius | 24px |
| cardPadding | 20px |
| inputHeight | 52px |
| buttonHeight | 52px |
| baseSpacing | 4px |
| sectionGap | 24px |

### Shadows (Light Mode Only — Dark Mode Uses Surface Elevation)
| Level | Value |
|-------|-------|
| card | `0 2px 8px rgba(0,0,0,0.04), 0 4px 24px rgba(0,0,0,0.08)` |
| modal | `0 -4px 24px rgba(0,0,0,0.12)` |
| fab | `0 4px 16px rgba(0,0,0,0.15)` |

## Rules
- NEVER hardcode colors — use theme system
- NEVER hardcode text styles — use theme typography
- NEVER hardcode dimensions — use design system constants
- All components must work in both light and dark mode
- All interactive elements minimum 44dp touch/click target
