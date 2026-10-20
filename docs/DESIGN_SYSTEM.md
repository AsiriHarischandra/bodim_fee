# BoardMate — Design System (Purple & White)

> Visual reference: the "BoardMate UI" design canvas (style guide + owner and member screens).
> These values become Tailwind theme tokens in Phase 5 (`apps/web/tailwind.config.ts`).

## 1. Principles
1. **White for reading, light purple for space.** Cards and forms are white; the app background is purple-50.
2. **One strong purple element per screen** (main button or hero card) so the eye knows where to go.
3. **Status colours carry meaning**, always with a text label (accessible for colour-blind users).
4. **Mobile-first for members**, desktop-first for owners.
5. Text contrast ≥ 4.5:1 (WCAG AA). Touch targets ≥ 44 px.

## 2. Colour tokens

### Brand purple scale
| Token | Hex | Use |
|---|---|---|
| `primary-50`  | `#F7F5FF` | App background (the "white space") |
| `primary-100` | `#EDE9FE` | Tinted panels, hover, secondary button, focus halo |
| `primary-200` | `#DDD6FE` | Input borders, outline button border |
| `primary-300` | `#C4B5FD` | Disabled, dashed upload border |
| `primary-400` | `#A78BFA` | Charts, sidebar badges |
| `primary-500` | `#8B5CF6` | Charts, "Under review" bar |
| `primary-600` | `#7C3AED` | Links |
| `primary-700` | `#6D28D9` | **Primary** — main buttons, hero card, active states |
| `primary-800` | `#5B21B6` | Pressed, text on tinted panels |
| `primary-900` | `#4C1D95` | Active sidebar item, headings on tint |
| `primary-950` | `#2E1065` | Sidebar, login brand panel |

### Neutrals
| Token | Hex | Use |
|---|---|---|
| `surface` | `#FFFFFF` | Cards, forms |
| `border` | `#E9E3FB` | Card borders, dividers |
| `text` | `#1E1033` | Body text (purple-tinted near-black) |
| `text-muted` | `#5B5470` | Captions, labels |

### Payment status
| Status | Text | Background |
|---|---|---|
| Paid | `#047857` | `#ECFDF5` |
| Partially paid | `#B45309` | `#FFFBEB` |
| Under review | `#5B21B6` | `#EDE9FE` |
| Pending | `#475569` | `#F1F5F9` |
| Overdue | `#B91C1C` | `#FEF2F2` |
| Rejected | `#9F1239` | `#FFF1F2` |

## 3. Typography
Font: **Plus Jakarta Sans** (Google Fonts), weights 400/500/600/700/800. Numbers use `font-variant-numeric: tabular-nums` so amounts line up in tables.

| Style | Size / weight |
|---|---|
| H1 | 30–36 / 800, letter-spacing −0.02em |
| H2 | 18–24 / 700 |
| H3 | 16–18 / 600 |
| Body | 15 / 400 |
| Caption | 13 / 400, `text-muted` |
| Amount (hero) | 30–36 / 800 |

## 4. Shape and spacing
- Spacing scale: 4 px base (4, 8, 12, 16, 20, 24, 32, 40, 56, 64).
- Radius: inputs/buttons 12, cards 20, pills 999.
- Borders 1 px `border`; focus = 1.5 px `primary-700` + 3 px `primary-100` outline.

## 5. Components
| Component | Spec |
|---|---|
| Primary button | h 44–52, `primary-700` bg, white 600–700 text |
| Secondary button | `primary-100` bg, `primary-800` text |
| Outline button | white bg, `primary-200` border, `primary-800` text |
| Danger button | `#B91C1C` (solid or outline) — reject only |
| Status badge | pill h 24–28, status colours, dot + label |
| Stat tile | white card, label 13/600 muted, value 30/800, progress bar `primary-100` track |
| Hero card | `primary-700` bg, white text, one per screen |
| Sidebar | `primary-950`, items 44 px, active `primary-900` |
| Mobile tab bar | 4 tabs, active `primary-700` |

## 6. Screens designed
Owner: Dashboard, Verify payments. Member (mobile 390 px): Home, Submit payment. Shared: Sign in.

## 7. In code (Phase 5)
Tokens go into `tailwind.config.ts` as `colors.primary.{50..950}`, `colors.status.*`, so the UI uses classes like `bg-primary-700` instead of hex values. Changing the brand = changing one file.
