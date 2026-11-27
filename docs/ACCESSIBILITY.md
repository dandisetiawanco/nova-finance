# Accessibility & Financial UX Audit

Accessibility checks were applied continuously during design execution (Anti-Slop Mode 1: DURING) using mathematical WCAG 2.x relative-luminance computation, Astryx accessibility guidance, and 2x visual inspection of rendered PNG screens.

*Scope note*: These checks verify the static design tokens, typography contrast, touch targets, and component states inside FigCraft. Formal assistive-technology testing (VoiceOver, TalkBack, dynamic font scaling at 200%, and keyboard tab traversal) must be re-verified when the Flutter application is implemented.

## 1. Computed WCAG 2.2 AA Color Contrast Audit

Every core foreground/background pairing was computed with the WCAG 2.x contrast formula (`(L1 + 0.05) / (L2 + 0.05)`):

| Pairing | Foreground | Background | Ratio | Normal Text (`4.5:1`) | Large Text (`3.0:1`) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Primary ink on Soft White | `#101512` | `#F7F9F6` | `17.43:1` | PASS | PASS |
| Primary ink on Pure White | `#101512` | `#FFFFFF` | `18.45:1` | PASS | PASS |
| Secondary ink on Soft White | `#4F5A52` | `#F7F9F6` | `6.80:1` | PASS | PASS |
| Secondary ink on Pure White | `#4F5A52` | `#FFFFFF` | `7.20:1` | PASS | PASS |
| Accessible green on White | `#117A37` | `#FFFFFF` | `5.44:1` | PASS | PASS |
| Accessible green on Fresh Mint | `#117A37` | `#DDF8E7` | `4.83:1` | PASS | PASS |
| Deep Forest on Fresh Mint | `#123C2B` | `#DDF8E7` | `10.93:1` | PASS | PASS |
| White on Deep Forest | `#FFFFFF` | `#123C2B` | `12.30:1` | PASS | PASS |
| Electric Lime on Deep Forest | `#B7F34D` | `#123C2B` | `9.34:1` | PASS | PASS |
| Near Black on Electric Lime | `#101512` | `#B7F34D` | `14.01:1` | PASS | PASS |
| Error red on White | `#C82D2D` | `#FFFFFF` | `5.43:1` | PASS | PASS |
| Dark text on Obsidian Forest | `#F4F7F4` | `#0B100D` | `17.78:1` | PASS | PASS |
| Dark muted on Forest Charcoal | `#9BB0A3` | `#121B16` | `7.65:1` | PASS | PASS |
| Electric Lime on Obsidian | `#B7F34D` | `#0B100D` | `14.57:1` | PASS | PASS |
| Emerald on Forest Charcoal | `#4ADE80` | `#121B16` | `10.09:1` | PASS | PASS |
| Dark error on Forest Charcoal | `#F87171` | `#121B16` | `6.36:1` | PASS | PASS |

### Key Contrast Decision Made During Audit
- `#FFFFFF` on Primary Green `#16A34A` measures **`3.30:1`** (passes Large Text `3.0:1`, fails Normal Text `4.5:1`).
- Consequently, `#16A34A` is reserved for graphical fills, progress bars, chart strokes, and icons, while normal-text buttons use **Deep Forest `#123C2B`** (`12.30:1` with white text) or **Electric Lime `#B7F34D`** (`14.01:1` with near-black ink), and small green text uses **`#117A37`** (`5.44:1` on white).

## 2. Financial UX & Non-Color Signal Verification

- **Never Color Alone**:
  - Positive inflows carry both `+` sign prefixes and `#117A37` / `#4ADE80` ink; expenses carry `-` prefixes.
  - Completed receipts combine `#DDF8E7` surface, checkmark vector, and explicit `"Completed · Settled"` label.
  - Error states combine `#FFF4F4` / `#C82D2D` border, `!` marker, specific failure cause, and a recovery button (`Adjust card cap`).
  - Selected filters and tabs combine solid background fill, bold typography weight, and top bar or checkmark indicators.
- **Touch Targets & Safe Areas**: All primary CTA buttons (`48 - 54 px` tall), icon buttons (`44 - 48 px`), back buttons (`44 x 44 px`), and bottom navigation items respect iOS safe areas (`48 px` top status bar, `80 px` bottom tab bar with home indicator clearance).
- **Form Clarity**: Every input carries a persistent visible label above the field (never placeholder-only labels) and a `2.5 px` focused ring (`>= 3:1`) documented on `DS 03 — Component & Data States`.

## 3. Known Design-Phase Limitations

- Screen reader semantic trees (`aria-label` / Flutter `Semantics`), VoiceOver focus order, and 200% dynamic text-size reflow are specifications for future engineering implementation rather than runtime-verified behaviors in a `.figcraft` file.
- The prototype does not simulate on-screen iOS keyboards scrolling bottom inputs into view; Flutter implementation must use `resizeToAvoidBottomInset` and scroll-into-view padding.
