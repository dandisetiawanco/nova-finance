# Design Engineering Workflow

NOVA Finance was produced using a live, tool-assisted design engineering pipeline inside **FigCraft Desktop** orchestrated by **Google Antigravity**.

## Active Ecosystem and Actual Roles

| Tool / Skill | Actual Role During Production |
| :--- | :--- |
| **Google Antigravity** | Coordinated design architecture, MCP execution, WCAG contrast scripting, visual audits, and repository packaging. |
| **FigCraft Desktop (`v0.18.1`)** | Live macOS design application running on loopback control port `127.0.0.1:7979`, rendering every frame and edit visibly in real time. |
| **FigCraft MCP (`figcraft-mcp`)** | Executed live `batch`, `run_command`, `variable.create`, `component.createMultiple`, `proto.interaction.add`, `view.zoomSelection`, `view.zoomFit`, `save_file`, and `export` calls with `85 ms` step streaming (`FIGCRAFT_STREAM_STEPS=1`). |
| **Astryx CLI (`@astryxdesign/cli`)** | Inspected design principles (`astryx docs principles`, `astryx docs tokens`, `astryx docs layout`) and component specs (`Button`, `TextInput`, `SegmentedControl`, `ProgressBar`) to ground component anatomy, edge-to-edge list rows, controlled form labels, and focus ring contrast without copying Astryx's default visual styling. |
| **Anti-Slop (`Mode 1: DURING`)** | Applied continuously across `antislop`, `antislop-ui`, `antislop-layoutmobile`, `antislop-human`, `antislop-copywriting`, and `figcraft-anti-slop` with declared dials `ENERGY 3 / RHYTHM 3 / MOTION 2`. |

## Step-by-Step Execution Sequence

1. **Live Backend Verification**: Verified `figcraft/inspect_ui` returned live Desktop window state (`windows[0].focused: true`, no headless fallback) before creating any layers.
2. **Foundations & Variables First**: Created all 6 document pages, 21 native Light/Dark and Scale variables, and the `01 — Brand Direction` board. Verified WCAG 2.2 AA contrast ratios via Python luminance checks before building screens.
3. **Flagship-First Validation**: Built `04 — Financial Home` first, exported it at 2x resolution, inspected the rendered PNG, and fixed 4 micro-alignment issues (virtual card label clearance, budget spacing, right-aligned transaction amounts, and Brand Direction table rows) before expanding.
4. **Full 15-Screen Light Mode Expansion**: Streamed the remaining 14 light screens in manageable batches (`390 x 844 px` on a structured 5x3 grid) to maintain responsive performance on an 8 GB Intel MacBook.
5. **Design System & Native Components**: Built Foundations, Core Components, and all 9 Interactive/Data States on `04 — Design System`, promoting 13 core frames to native reusable FigCraft Components.
6. **Redesigned Dark Mode**: Built 5 key screens on `03 — Mobile App / Dark` using an Obsidian Forest and Forest Charcoal elevation ramp rather than inverted light colors.
7. **Interactive Prototyping**: Built `05 — Motion & Prototype` and wired 47 live `proto.interaction.add` transitions across all 15 light screens.
8. **Portfolio Showcase & Final Audit**: Built `06 — Product Showcase` (Editorial Cover, Dual-Theme & Data Viz board, and 4:5 Social Teaser), visually audited every exported board, fixed 3 additional minor light-mode alignment details caught during full-grid inspection, saved `NOVA-Finance.figcraft`, and exported 32 PNG assets plus 12 original SVGs.
