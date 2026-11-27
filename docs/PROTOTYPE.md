# Interactive Prototype & Motion Specification

NOVA Finance defines a 4-tier motion timing model on page `05 — Motion & Prototype` and implements **47 live wired prototype transitions** across all 15 mobile screens on `02 — Mobile App / Light` inside `design/NOVA-Finance.figcraft`.

## Motion Timing Architecture

| Band | Duration Range | Applied Default | Intended Interactions |
| :--- | :--- | :--- | :--- |
| Micro-interactions | `120 - 180 ms` | `150 ms` | Button tap feedback, toggle switches, filter chip selection |
| Component transitions | `180 - 250 ms` | `200 - 220 ms` | Bottom tab crossfade (`dissolve`), SegmentedControl thumb slide, focus rings |
| Screen transitions | `250 - 350 ms` | `260 - 320 ms` | Forward/back `push` navigation, `smartAnimate` card and goal expansions |
| Celebration moments | `350 - 500 ms` | `420 ms` | `09 — Transfer Successful` confirmation reveal (`smartAnimate`) |

All prototype links use `easeOut` easing. Native engineering implementations should cap non-essential transitions to `<= 200 ms` crossfades under `prefers-reduced-motion: reduce`.

## Wired Prototype Flows (`47` Verified Connections)

### 1. Onboarding & Authentication
- `01 Splash` (`Open NOVA Finance`) -> `02 Onboarding` (`dissolve`, `300 ms`)
- `02 Onboarding` (`Skip` / `Continue to Sign In`) -> `03 Sign In` (`push left`, `280 ms`)
- `03 Sign In` (`Back`) -> `02 Onboarding` (`push right`, `260 ms`)
- `03 Sign In` (`Sign in to NOVA` / `Continue with Face ID`) -> `04 Financial Home` (`smartAnimate`, `300 - 320 ms`)

### 2. Primary Bottom Navigation Hub (`dissolve`, `200 ms`)
All five root tabs interconnect bidirectionally across their bottom navigation bars:
- `04 Financial Home` <-> `05 Digital Cards` <-> `06 Transaction History` <-> `10 Financial Analytics` <-> `14 Profile`

### 3. Transfers, Receipts, Goals, Alerts, and Security
- `04 Financial Home` (`Send` CTA) -> `08 Send Money` (`push left`, `280 ms`) -> `09 Transfer Successful` (`smartAnimate`, `420 ms`) -> `04 Financial Home` (`smartAnimate`, `300 ms`) or `07 Transaction Details` (`push left`, `260 ms`)
- `04 Financial Home` (Virtual Card) -> `05 Digital Cards` (`smartAnimate`, `300 ms`)
- `04 Financial Home` (Recent activity rows) & `06 Transaction History` (Row 1) -> `07 Transaction Details` (`push left`, `280 ms`) -> Back to `06 Transaction History` (`push right`, `260 ms`)
- `04 Financial Home` (Savings Goal preview / More) -> `11 Savings Goals` (`smartAnimate`, `280 ms`) -> `+ New goal` -> `12 Create Savings Goal` (`push left`, `280 ms`) -> `Create savings goal` (`smartAnimate`, `320 ms`) / Back (`push right`, `260 ms`) -> `11 Savings Goals`
- `04 Financial Home` (Bell button) -> `13 Notifications` (`push left`, `260 ms`) -> Back to `04 Financial Home` (`push right`, `260 ms`), plus Transfer Alert -> `07 Transaction Details`
- `14 Profile` (`Settings & security controls`) -> `15 Settings & Security` (`push left`, `280 ms`) -> Back to `14 Profile` (`push right`, `260 ms`)
- `14 Profile` (`Sign out of NOVA`) -> `03 Sign In` (`dissolve`, `280 ms`)

## Engine Capabilities & Honest Limitations

- **Supported & Wired in FigCraft `v0.18.1`**: `onClick` triggers with `navigate` actions, `smartAnimate`, `push` (`left`/`right`), `dissolve`, `durationMs`, and `easeOut` easing are wired and playable inside FigCraft Desktop's Present view.
- **Documented for Native Implementation Only**: OS biometric Face ID prompts, tactile haptics, interactive drag-to-scrub on `SegmentedControl`, and physics-based spring gestures are not natively simulated by the static prototype and are handed off as native engineering specs.
