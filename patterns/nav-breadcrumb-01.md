---
id: nav-breadcrumb-01
name: Breadcrumbs
status: draft
version: 0.1
phase: 1
owner: anton.malashkevych
last-reviewed: 2026-09-23
applies-to: [analytics, flo, policy-pulse, admin]
boundaries: [nav-tabs-01: open views, nav-cvbar-01: section navigation with back control]
related: [nav-shell-01, drill-in-01]
supersedes: []
kit-notes: ["Not present in the reference build; documented from the kit only"]
figma: https://www.figma.com/design/QWpZtLfVsUjbc99Lj3JJwJ/Kinetic-Platform---Atomic-Library-of-Elements?node-id=13282-182894
code: ""
---

# Breadcrumbs

## Anatomy
Single-line path from the root item to the current item. Kit variants: Levels (1 level, Multi levels) and Full Path (False, True).

```
1 level
[ Parad.. RMA / Transactions Scope                 ]

multi levels
[ Parad.. RMA  [/ (folder) File Tree]  / Transac..  (i) ]

multi levels, full path on
[ Parad.. RMA  [/ (folder) File Tree]  / Transac..  (i) ]  +--------------------------------------+
                                                          | Paradise RMA / Folder 1 / Folder 1.2 |
                                                          | / Transactions Scope                 |
                                                          +--------------------------------------+
```

| Part | Kit component | Tokens | Role / name |
|---|---|---|---|
| Container | Breadcrumbs | `overlay/ghost-pill-bg-interactive` | `nav` |
| Ancestor | text | `text/primary`, underlined, `font-size/sm` | link |
| Separator | text | `text/primary`, "/" | decorative |
| Collapsed middle (Multi levels) | text, icon folder-l-menu | `accent/interactive`, `neutral/white`, `radius/xs`; content "/ File Tree" | `button` |
| Current | text | `brand/primary`, underlined, `font-size/sm` | `aria-current="page"` |
| Full path trigger (Multi levels) | icon label | `text/primary` | `button` |
| Full path tooltip (Full Path=True) | Tooltips/Black | `bg/card`, `radius/lg`; ancestors `text/primary`, current `brand/primary`, all underlined | `tooltip` |

## Behavior
- Root and current are always visible; with more than two levels the intermediate levels collapse into one "File Tree" segment.
- Long labels truncate with ".." inline; the full path tooltip shows labels untruncated.
- The full path tooltip appears from the trailing icon in the Multi levels variant only.
- Current is the last segment and is not a link.

## Changelog
- 0.1 2026-09-23: created from Breadcrumbs component (3 variants).
