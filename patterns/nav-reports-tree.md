---
id: nav-reports-tree
name: Reports tree
status: draft
version: 0.1
phase: 1
owner: anton.malashkevych
last-reviewed: 2026-09-23
applies-to: [analytics]
boundaries: [nav-sidebar: global destinations, nav-content-tabs: open views, panel-base: panel base]
related: [nav-breadcrumb, search]
supersedes: []
kit-notes: ["Not present in the reference build; documented from the kit only", "Panels/Reports uses Menu items/Left menu items for tree rows; Navigation bars/Left menu is deprecated but this item component is still in use"]
figma: https://www.figma.com/design/QWpZtLfVsUjbc99Lj3JJwJ/Kinetic-Platform---Atomic-Library-of-Elements?node-id=13282-181812
code: ""
---

# Reports tree

## Anatomy
A panel listing report folders as a collapsible tree. Two states: Default (roots collapsed) and Opened (a folder expanded, breadcrumbs shown above the search).

```
default                     opened
+------------------------+  +------------------------+
| Reports             x  |  | Reports             x  |
| [Search             q] |  | Parad.. RMA / Transac..|
|------------------------|  | [Search             q] |
| > (f) Paradise DMA     |  |------------------------|
| > (f) Paradise Denial  |  | > (f) Paradise DMA     |
| > (f) Paradise RMA     |  | > (f) Paradise Denial  |
| > (f) Enterprise Mgr   |  | v (f) Paradise RMA     |
+------------------------+  |    > (f) My Reports    |
                            |    v (f) Ad-hoc Reports|
                            |        (r) Accounts S..|
                            |        (r) Charges Su..|
                            |    > (f) Dashboards    |
                            | > (f) Enterprise Mgr   |
                            +------------------------+
```

| Part | Kit component | Tokens | Role / name |
|---|---|---|---|
| Container | Panels/Reports | `bg/card`, `radius/lg`, `shadow-panel-dark` | `nav` "Reports" |
| Header | Headers/Panels | title `text/primary`, `font-size/md`, `font-weight/semibold`; divider below | heading; close `button` |
| Close | Buttons/Icon button/Additional | `overlay/ghost-pill-bg-interactive`, `radius/md`; icon close-small | `button` |
| Breadcrumbs (Opened) | Breadcrumbs | see nav-breadcrumb | |
| Search | Inputs/Search field | `bg/card`, `lines/section`, `radius/md`, `text/muted`; icon search | textbox, placeholder "Search" |
| Section divider | Foundations/Divider/Horizontal | | |
| Folder row, collapsed | Menu items/Left menu items | chevron dropdown-small rotated closed; icon folder-l-menu; label `text/primary`, `font-size/sm` | `treeitem`, `aria-expanded="false"` |
| Folder row, expanded | Menu items/Left menu items | chevron rotated open; label `brand/primary` | `treeitem`, `aria-expanded="true"` |
| Report row | Menu items/Left menu items | icon report-in-list; label `text/primary`; no chevron | `treeitem` |

## Behavior
- Root folders are collapsed in the Default state.
- Expanding a folder colors its label `brand/primary` and indents its children one level per depth.
- Reports are leaves: no chevron, report icon, not expandable.
- Long labels truncate with "..".
- In the Opened state, breadcrumbs render between the header and the search field and show the path to the expanded folder.
- Search sits above the tree and applies to the tree below it.

## Changelog
- 0.1 2026-09-23: created from Panels/Reports (Default, Opened).
