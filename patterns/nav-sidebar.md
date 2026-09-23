---
id: nav-sidebar
name: Sidebar
status: draft
version: 0.3
phase: 1
owner: anton.malashkevych
last-reviewed: 2026-09-18
applies-to: [shell]
boundaries: [nav-toolbar: view actions, nav-ana-panel: Ana conversation, nav-user-menu: user menu contents]
related: [nav-shell, nav-alerts, nav-help, save-favorites]
supersedes: []
kit-notes: ["KIT REQUEST: deprecate Navigation bars/Left menu in favor of Navigation bars/Side bar", "TOKEN REQUEST: layout/sidebar-collapsed, layout/sidebar-expanded, motion/duration-base"]
figma: https://www.figma.com/design/QWpZtLfVsUjbc99Lj3JJwJ/Kinetic-Platform---Atomic-Library-of-Elements?node-id=1-15
code: "@kinetic-ui/nav-bars SideBar; reference build https://antonmalashkevych.github.io/kinetic_ux/"
---

# Sidebar

## Anatomy
Leftmost column of the shell, full height. Three regions: header, scrolling item region, footer pinned to the bottom. Two states: collapsed (icons) and expanded (icons and labels).

```
collapsed          expanded
+----+             +------------------------+
| K  |             | K  Kinetic          <| |
| <| |             | + New conversation     |  Ana shortcuts, only while the
| +  |             | h History              |  Ana panel is collapsed
| h  |             | [Search items...     ] |
|----|             | Browse Recent Most Star|
| o  |             | Pin starred to top  (o)|
| o  |             | o Command Center     * |
| o  |             | o Live Insight Feed  * |
| o  |             | o Favorites          * |
|----|             | o Last Opened        * |
| o  |             | TOOLS                  |
| o  |             | o Denial Resolution    |
| o  |             | o Patient Access       |
|    |             | o Alerts               |
| a  |             | a Ask Ana        ( / ) |
| ?  |             | ? Help                 |
| AM |             | AM Anton M.            |
+----+             +------------------------+
```

| Part | Kit component | Tokens | Role / name |
|---|---|---|---|
| Container | Navigation bars/Side bar | `bg/surface-deep`, `lines/card`, `radius/card`; width `layout/sidebar-collapsed` or `layout/sidebar-expanded` | `nav` "Primary navigation" |
| Brand mark | Primitives/Avatars | `brand/primary`, `neutral/white`, `radius/control` | decorative |
| Product name (expanded) | text | `text/primary` | "Kinetic" |
| Toggle | Buttons/Icon button | `icon/tertiary`; hover `state/hover`; `radius/control`; icon panel-left | "Expand navigation" / "Collapse navigation" |
| Ana shortcuts (Ana panel collapsed) | Menu items/Side bar/Item card | as Item | "New conversation"; "Conversation history" (collapsed) or "History" (expanded) |
| Search field (expanded) | Inputs/Search field | `bg/surface-subtle`, `border/default`, `text/placeholder`; focus `border/active`, `state/focus` | textbox "Search items", placeholder "Search items..." |
| Segmented filter (expanded) | Tabs/Segments control/Default | container `control/segment`, `lines/hairline`, `radius/control`; selected `bg/surface-muted` `text/primary`; unselected `text/muted`, hover `control/segment-hover` | `radiogroup` "Filter navigation items": Browse, Recent, Most used, Starred |
| Pin switch (expanded, Browse, no search) | Switcher/General | on `accent/interactive`, `radius/pill`; label `text/muted` | `switch` "Pin starred to top" |
| Item | Menu items/Side bar/Item card | default `text/secondary`, `radius/control`; hover `state/hover`; current `state/selected`, `text/primary`, icon `accent/interactive-soft` | `button`, `title` = label; current `aria-current="page"` |
| Star (expanded, core items) | Buttons/Icon button | off `icon/tertiary`; on `brand/primary`; hover `state/hover` | `button` `aria-pressed`, "Star <label>" / "Unstar <label>" |
| Group label (expanded) | text | `text/decor` | "TOOLS" |
| Empty result (search) | text | `text/muted` | `Nothing matches "<query>".` |
| User | Primitives/Avatars | `bg/surface-emphasis`, `text/primary`, `radius/pill` | initials; name when expanded |

Items and icons (reference build): Command Center layout-dashboard; Live Insight Feed rss; Favorites star; Last Opened rotate-ccw-clock; Denial Resolution Copilot shield-check; Patient Access Copilot clipboard-list; Alerts bell; Ask Ana activity; Help circle-question-mark.

## Behavior
- Default state is collapsed. State is stored browser-local and restored on load.
- The toggle is the only control that changes state. Width change is animated with `motion/duration-base`.
- Header and footer are fixed; only the item region scrolls.
- Exactly one item is current. Labels are single line and truncate.
- Stars exist on core items only. Starring does not navigate.
- With the pin switch on and Browse selected, starred items appear first in the core group.
- Search and the segmented filter apply to core items only; TOOLS and footer are unaffected. Recent lists visited core items; Starred lists starred core items.
- The pin switch is shown only with Browse selected and an empty search.
- Ask Ana focuses the Ana input; `/` outside a text field does the same.
- Ana shortcuts appear in both sidebar states while the Ana panel is collapsed, directly under the header.

## Changelog
- 0.3 2026-09-18: reduced template; parts table; icons, scroll regions, finder scope, empty result, and persistence added from reference build.
- 0.2 2026-09-18: observed behavior only.
- 0.1 2026-09-18: created from Kinetic Side bar and reference build.
