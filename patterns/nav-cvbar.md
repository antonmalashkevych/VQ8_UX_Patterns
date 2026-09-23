---
id: nav-cvbar
name: CV navigation bar
status: proposed
version: 0.1
phase: 1
owner: anton.malashkevych
last-reviewed: 2026-09-18
applies-to: [admin]
boundaries: [nav-sidebar: destinations, nav-content-tabs: open views]
related: [nav-shell, permissions-ui]
supersedes: []
kit-notes: ["Not present in the reference build; documented from the kit only"]
figma: https://www.figma.com/design/QWpZtLfVsUjbc99Lj3JJwJ/Kinetic-Platform---Atomic-Library-of-Elements?node-id=1-15
code: "@kinetic-ui/nav-bars CVNavBar backButton title"
---

# CV navigation bar

## Anatomy
Horizontal bar across the top of an app's content: back control with the parent title, then section segments, one active. A trailing segment with chevron-down exists in the kit, hidden by default.

```
+--------------------------------------------------------------------------+
| <- UM   ACTION PANEL  [FLO PERMISSIONS]  FLO ACTION PANEL MANAGEMENT ... |
+--------------------------------------------------------------------------+
```

| Part | Kit component | Tokens | Role / name |
|---|---|---|---|
| Container | Navigation bars/CV navigation bar | `shadow-panel-dark` | `nav` |
| Back | Tabs/Atoms/Segment | icon return-arrow; `text/muted` | `button`, parent title as label ("UM") |
| Segment, inactive | Tabs/Atoms/Segments control/Rounded | `text/muted`, `radius/lg` | `tab` |
| Segment, active | Tabs/Atoms/Segments control/Rounded | `brand/primary`, `neutral/white`, `radius/lg` | `tab`, `aria-selected` |
| Overflow (hidden) | Tabs/Atoms/Segment | icon chevron-down | `button` |

## Behavior
- Exactly one segment is active.
- Segment labels are uppercase.
- Back returns to the parent named in its label.

## Changelog
- 0.1 2026-09-18: created from Navigation bars/CV navigation bar.
