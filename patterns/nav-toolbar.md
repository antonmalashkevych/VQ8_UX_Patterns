---
id: nav-toolbar
name: Toolbar
status: proposed
version: 0.1
phase: 1
owner: anton.malashkevych
last-reviewed: 2026-09-18
applies-to: [shell]
boundaries: [nav-sidebar: destinations, nav-user-menu: user menu contents]
related: [nav-shell, export-share, save-favorites]
supersedes: []
kit-notes: ["KIT REQUEST: rename Navigation bars/Right menu to Toolbar", "Not present in the reference build; documented from the kit only"]
figma: https://www.figma.com/design/QWpZtLfVsUjbc99Lj3JJwJ/Kinetic-Platform---Atomic-Library-of-Elements?node-id=1-15
code: "@kinetic-ui/nav-bars NavRail side=right"
---

# Toolbar

## Anatomy
Rightmost column of the shell, full height, icon-only. Three regions: user avatar at top, action items, feedback pinned to the bottom.

```
+----+
| M  |  avatar
|----|
| *  |  favorites
| r  |  reload
| ap |  action panel
| x  |  excel
| p  |  pdf
| m  |  show-ap
|    |
| fb |  feedback
+----+
```

| Part | Kit component | Tokens | Role / name |
|---|---|---|---|
| Container | Navigation bars/Right menu | `shadow-panel-dark` | `toolbar` |
| Avatar | Menu items/Profile | Primitives/Avatars; `neutral/white` initial | `button` |
| Action item | Menu items/Bar item | `radius/lg`; icons favorites-r-menu, reload-r-menu, action-panel-r-menu, excel-r-menu, pdf-r-menu, show-ap | `button` |
| Feedback | feedback-r-menu | as Action item | `button` |

## Behavior
- Items are icon-only.
- Feedback is the last item, pinned to the bottom.
- The kit Right menu contains a hidden `Ana/Side bar` instance; Ana is not part of the toolbar (nav-ana-panel).

## Changelog
- 0.1 2026-09-18: created from Navigation bars/Right menu.
