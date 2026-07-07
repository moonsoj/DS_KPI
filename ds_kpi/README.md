# DS_KPI — V.Doc Pro Design System KPI Dashboard

A dashboard that tracks **measurable** improvements to the V.Doc Pro design system.

Every design-system change is proven per screen by comparing **AS-IS** (the current shipped build) against **TO-BE** (the same screen rebuilt with the new system) on a fixed set of KPIs. It is a closed-loop measurement, not a subjective before/after.

The goal is not visual change. It is **consistency and conformance**. Most screens look nearly identical — the value is in the invisible metrics (letter-spacing uniformity, line-height regularity, off-scale sizes, style-count) that improve.

## View

- Open `index.html` in any browser, or visit the published GitHub Pages URL.
- Left nav: **Overview** + one page per verified screen. Each screen page shows AS-IS vs TO-BE side by side, the KPI table, and an auto-generated change log.
- `index.html` is fully self-contained (all screen images embedded). No server or build step required.

## Modules

The dashboard is one place for the whole design system. Each foundation module is measured the same way and adds its screens to the same dashboard.

| Module | Status |
|---|---|
| Typography | In progress — 7 / 9 screens |
| Color | Planned |
| Icons | Planned |
| Spacing | Planned |

Each module defines its own KPIs and its own capture/measurement method.

## Typography KPIs

| # | KPI | Target |
|---|---|---|
| 1 | Token conformance — % of text on the scale with a valid weight | ≥ 95% |
| 2 | Distinct style count — unique (size · weight · line-height · letter-spacing) combos | minimize |
| 3 | Letter-spacing rule count | 1 |
| 4 | Letter-spacing uniformity — % at −0.5% | 100% |
| 5 | Line-height regularity — % matching the token line-height | 100% |
| 6 | Off-scale size count — sizes outside the scale | 0 |

## Method (closed loop)

1. **Capture** a screen from the running app: a screenshot + a structure JSON (each text element's content, position, and computed font size / weight / line-height / letter-spacing).
2. **Measure AS-IS** directly from the JSON.
3. **Rebuild** the screen as HTML using the new tokens.
4. **Re-measure** the rebuilt HTML with the same script.
5. **Compare** AS-IS vs TO-BE and add the result to the dashboard.

The measurement doubles as a quality gate — it flags any element that does not conform (it has already caught reconstruction defects that were then fixed).

## Adding a screen

Add one entry to the `COMPLETED` array in `index.html` with the screen's AS-IS/TO-BE KPI values and its two image paths. The overview summary, progress bar, KPI rollup, and change log all render automatically from the data.

## Notes

- Screens use **dummy / test data only** — no real patient information.
- Typography renders in Pretendard (via CDN); screen images are pre-rendered and embedded.
- Scope is the design system foundation only. Product logic and content are out of scope.
