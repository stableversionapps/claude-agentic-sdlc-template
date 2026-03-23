# Design Tokens Reference

<!-- Customize all values below for your project -->

## Colors

| Token | Light | Dark | Usage |
|-------|-------|------|-------|
| Primary | `[YOUR_PRIMARY]` | `[YOUR_PRIMARY]` | Brand CTAs, key headers |
| Secondary | `[YOUR_SECONDARY]` | `[YOUR_SECONDARY]` | Accents, links (sparingly) |
| Background | `[YOUR_LIGHT_BG]` | `[YOUR_DARK_BG]` | Page background |
| Surface | `[YOUR_LIGHT_SURFACE]` | `[YOUR_DARK_SURFACE]` | Cards, sheets |
| Surface Elevated | `[VALUE]` | `[VALUE]` | Grouped backgrounds |
| Success | `#10B981` | `#10B981` | Positive outcomes (contextual) |
| Error | `#EF4444` | `#EF4444` | Errors, negative (contextual) |
| Warning | `#F59E0B` | `#F59E0B` | Warnings (contextual) |

## Typography

| Style | Size | Weight | Use |
|-------|------|--------|-----|
| displayLarge | 32sp | Bold 700 | Hero numbers, page titles |
| headlineMedium | 24sp | SemiBold 600 | Section titles |
| titleMedium | 18sp | Medium 500 | Card headers |
| bodyLarge | 16sp | Regular 400 | Body text |
| bodyMedium | 14sp | Regular 400 | Secondary text |
| labelSmall | 12sp | Regular 400 | Captions, labels |

## Spacing (8pt Grid)

| Token | Value | Usage |
|-------|-------|-------|
| xs | 4px | Tight internal spacing |
| sm | 8px | Related element spacing |
| md | 16px | Standard content spacing |
| lg | 24px | Section separation |
| xl | 32px | Major section gaps |
| xxl | 48px | Page-level separation |

## Dimensions

| Token | Value |
|-------|-------|
| cardRadius | 20px |
| buttonRadius | 12px |
| modalRadius | 24px |
| cardPadding | 20px |
| inputHeight | 52px |
| buttonHeight | 52px |
| minTouchTarget | 44dp |

## Shadows

| Level | Light Mode | Dark Mode |
|-------|-----------|-----------|
| card | `0 2px 8px rgba(0,0,0,0.04)` | none (use surface elevation) |
| modal | `0 -4px 24px rgba(0,0,0,0.12)` | none (use surface elevation) |
| fab | `0 4px 16px rgba(0,0,0,0.15)` | none (use surface elevation) |

## Rules
- NEVER hardcode colors — use theme system
- NEVER hardcode text styles — use theme typography
- NEVER hardcode dimensions — use design system constants
- All components must work in both light and dark mode
- All interactive elements minimum 44dp touch/click target
