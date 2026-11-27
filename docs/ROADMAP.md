# Development Roadmap

> **Important:** Every engineering item below is **planned future work**. None of these mobile, backend, or security services are implemented in this design repository yet.

## Phase 1: Design Foundation (Completed in This Repository)

- Editable FigCraft project (`design/NOVA-Finance.figcraft`) with 6 pages, 20 mobile screens (15 Light + 5 Dark), 13 native components, 21 Light/Dark & Scale variables, and 47 wired prototype flows.
- High-resolution 2x visual exports, original SVG brand marks/icons/illustrations, and WCAG 2.2 AA design-level contrast audit.

## Phase 2: Flutter Mobile Application (Planned)

- Initialize a clean Flutter workspace targeting iOS and Android with responsive layout scaling beyond `390 x 844 px`.
- Translate the `21` NOVA FigCraft variables (`NOVA Colors` Light/Dark and `NOVA Scale`) into strongly typed `ThemeExtension` tokens.
- Implement core reusable widgets corresponding to the `13` design-system components with full interactive states (Default, Pressed, Selected, Focused, Disabled, Loading, Success, Error, Empty).
- Integrate `prefers-reduced-motion` (`MediaQuery.disableAnimations`) and screen-reader semantics (`Semantics`) across every control.

## Phase 3: Backend API & Core Ledger (Planned)

- Build an API service with double-entry ledger storage, idempotent transfer keys, and pagination for grouped transaction history.
- Expose read/write endpoints for virtual card spending limits, card freeze states, savings goals, and auto-contribution schedules.
- Generate downloadable PDF transaction receipts with verifiable reference numbers.

## Phase 4: Authentication & Account Security (Planned)

- Implement OAuth2 / OIDC authentication with passkeys and native biometric verification (`local_auth` for Face ID / Touch ID / Android BiometricPrompt).
- Add device session management, instant card freeze endpoints, and privacy blur on app backgrounding.

## Phase 5: Analytics, Savings Automation, and Notifications (Planned)

- Implement weekly/monthly/yearly cash-flow aggregation and merchant categorization powering the `Analytics` charts.
- Add scheduled monthly/weekly/round-up transfers for `Savings Goals` with recalculated completion forecasts.
- Add push notification delivery for real-time spend authorizations, security logins, and goal milestones.
