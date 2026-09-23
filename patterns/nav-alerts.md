---
id: nav-alerts
name: Alerts panel
status: draft
version: 0.1
phase: 1
owner: anton.malashkevych
last-reviewed: 2026-09-23
applies-to: [shell]
boundaries: [nav-sidebar: the Alerts entry item, fb-toast: transient notifications, drill-panel: panel base]
related: [nav-sidebar, badge-semantics]
supersedes: []
kit-notes: ["Panels/Alerts has one variant (Dark/Light=False); the Text view of the Colors / Text switcher is not designed", "Not present in the reference build beyond the sidebar item"]
figma: https://www.figma.com/design/QWpZtLfVsUjbc99Lj3JJwJ/Kinetic-Platform---Atomic-Library-of-Elements?node-id=13282-181812
code: ""
---

# Alerts panel

## Anatomy
Panel opened from the Alerts item in the sidebar. Header, view switcher, donut chart by category, two totals, category table.

```
+------------------------+
| My Alerts           x  |
| [Colors] [Text 1]      |
|        (donut)         |
| [Total 4] [Triggered 1]|
| Category  Total Trigg. |
| o Red       1     1    |
| o Orange    1     0    |
| o Yellow    1     0    |
| o Lime      1     0    |
| o Green     0     0    |
+------------------------+
```

| Part | Kit component | Tokens | Role / name |
|---|---|---|---|
| Container | Panels/Alerts | `bg/card`, `shadow-panel-dark` | `dialog` or `region` "My Alerts" |
| Header | Headers/Panels | title `text/primary`; close Buttons/Icon button/Additional `overlay/ghost-pill-bg-interactive` | heading; close `button` |
| View switcher | Tabs/Segments control/Default (2 segments, Small) | selected `brand/primary`; default `bg/card` | `radiogroup`: Colors, Text |
| Donut | chart | ring `neutral/grey-green`; slices `semantic/error`, `semantic/warning`, `semantic/warning-soft`, `semantic/success` | `img` |
| Totals | tile | `overlay/ghost-pill-bg-interactive`; label and value `text/primary`; value `font-family/mono` | "Total", "Triggered" |
| Table header | Tables/Flo grid data field (Text) | | `columnheader`: Category, Total, Triggered |
| Table row | Tables/Flo grid data field (Priority, Text, Text) | row divider `lines/hairline` | `row`; priority cell carries the category color dot |

## Behavior
- Category colors in the table match the donut slices.
- Triggered is a subset of Total per category and in the totals tiles.
- The Text segment count badge shows the number of text alerts.

## Changelog
- 0.1 2026-09-23: created from Panels/Alerts.
