# NOVA Design System

The NOVA Design System is stored on pages `01 — Brand Direction` and `04 — Design System` inside `design/NOVA-Finance.figcraft`. Visual decisions follow the NGOPREK DIGITAL palette while adopting structural and accessibility patterns inspected from Meta's Astryx Design System CLI (`@astryxdesign/cli`).

## 1. Native FigCraft Variables (`21` Verified Tokens)

### Collection 1: `NOVA Colors` (`12` Variables, Modes: `Light` and `Dark`)

| Variable Name | Light Mode | Dark Mode | Intended Role |
| :--- | :--- | :--- | :--- |
| `brand/primary-green` | `#16A34A` | `#22C55E` | Brand fills, active progress bars, chart strokes, icons |
| `brand/electric-lime` | `#B7F34D` | `#B7F34D` | High-contrast primary send CTAs and focal card accents |
| `brand/fresh-mint` | `#DDF8E7` | `#163826` | Positive semantic tint surfaces and chart area fills |
| `brand/deep-forest` | `#123C2B` | `#164733` | Primary buttons (Light), virtual debit cards, hero banners |
| `surface/canvas` | `#F7F9F6` | `#0B100D` | Mobile screen background canvas |
| `surface/card` | `#FFFFFF` | `#121B16` | Elevated widget cards, inputs, and bottom navigation |
| `surface/elevated` | `#EEF3EC` | `#19261F` | Muted tracks, secondary badges, and segmented tracks |
| `text/primary` | `#101512` | `#F4F7F4` | Primary headings, balances, and body copy |
| `text/secondary` | `#4F5A52` | `#9BB0A3` | Captions, metadata, timestamps, and inactive labels |
| `text/brand-accessible` | `#117A37` | `#4ADE80` | Accessible green text for links, credits, and positive deltas |
| `border/subtle` | `#E3E9E2` | `#26382E` | Hairline dividers and quiet card outlines |
| `status/error` | `#C82D2D` | `#F87171` | Error states, destructive buttons, and card lock warnings |

### Collection 2: `NOVA Scale` (`9` Variables, Mode: `Default`)

- **Spacing (4pt/8pt rhythm)**: `space/xs` (`4`), `space/sm` (`8`), `space/md` (`16`), `space/lg` (`24`), `space/xl` (`32`).
- **Corner Radii**: `radius/sm` (`8`), `radius/md` (`12`), `radius/lg` (`18`), `radius/card` (`22`). Mobile device frames use `40px` outer corners.

## 2. Typography Architecture

Typography uses locally available macOS system typefaces and JetBrains Mono (referenced by family name in `.figcraft`, not redistributed):

| Role | Typeface & Weight | Size / Tracking | Usage |
| :--- | :--- | :--- | :--- |
| Financial Hero Balance | `Avenir Next Bold` | `38-48 px` / `-1.2` | Home balance, Send Money input, Transfer confirmation |
| Page Title | `Avenir Next Bold` | `26-32 px` / `-0.6` | Screen headers and onboarding headline |
| Section Heading | `Avenir Next Bold` / `Demi Bold` | `16-18 px` / `-0.2` | Recent activity, Card controls, Category breakdown |
| Ledger & Form Body | `Helvetica Neue Regular` / `Medium` | `14-15 px` / `0` | Transaction titles, input values, body explanations |
| Captions & Metadata | `Helvetica Neue Regular` | `11-12 px` / `+0.2` | Timestamps, category subtitles, budget caps |
| Tabular Codes & Card Numbers | `JetBrainsMonoNL Nerd Font Medium` | `12-16 px` | Fictional card numbers, Reference IDs, motion bands |

## 3. Mobile Grid & Elevation

- **Mobile Frame**: `390 x 844 px` with `48 px` top safe area, `20 px` horizontal margins, 4-column structural rhythm (`12 px` gutters), `80 px` bottom navigation bar, and `44 px` minimum interactive touch targets.
- **Elevation Discipline**: Flat `#FFFFFF` (Light) and `#121B16` (Dark) cards anchored by `1 px` hairline borders rather than drop shadows on every container. Dense transaction lists render as edge-to-edge rows with hairline dividers (aligned with Astryx layout rules).

## 4. Native Reusable FigCraft Components (`13` Verified Components)

All 13 components live on `04 — Design System` (`DS 02 — Core Components`) and are registered in FigCraft's Assets panel:

1. `Button / Primary Forest` (`#123C2B` / `#FFFFFF`)
2. `Button / Primary Lime` (`#B7F34D` / `#101512`)
3. `Button / Secondary Outlined` (`#FFFFFF` / `#CBD6CA` border)
4. `Button / Destructive` (`#FFF4F4` / `#C82D2D` border & ink)
5. `Button / Icon 48px` (48 x 48 px square icon target)
6. `Input / Text Field`
7. `Input / Search Field`
8. `SegmentedControl / NOVA` (`Week | Month | Year`)
9. `Card / NOVA Virtual Debit`
10. `Row / Transaction Ledger Item`
11. `Card / Savings Goal Widget`
12. `Navigation / Bottom Tab Bar`
13. `Chart / Cash Flow Area Component`

## 5. Interactive and Data States (`9` Documented States)

Board `DS 03 — Component & Data States` specifies all 9 states explicitly:

1. **Default**: Rest state with clear tap affordance.
2. **Pressed**: Darkened forest fill (`#092318`) with slight scale compression (`150 ms`).
3. **Selected**: Solid fill + bold text + checkmark symbol (never color alone).
4. **Focused**: `2.5 px` high-contrast `#16A34A` outer focus ring around `#123C2B` input border (`>= 3:1`).
5. **Disabled**: Muted `#E9EFE8` surface with prerequisite label ("Enter amount first").
6. **Loading**: Contextual progress bar + skeleton rows ("Syncing November transactions...").
7. **Success**: `#DDF8E7` surface, checkmark, settled reference ID, and "View receipt" CTA.
8. **Error**: `#FFF4F4` surface, `#C82D2D` border, alert prefix, specific cause (card limit reached), and "Adjust card cap" recovery CTA.
9. **Empty**: Custom vector icon, exact cause ("No transactions match 'Tokyo'"), and "Clear all filters" next step.
