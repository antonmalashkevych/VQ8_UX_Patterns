---
id: nav-content-tabs
name: Content tabs
status: draft
version: 0.2
phase: 1
owner: anton.malashkevych
last-reviewed: 2026-09-18
applies-to: [shell]
boundaries: [nav-sidebar: destinations, nav-cvbar: section navigation inside an app]
related: [nav-shell, save-favorites]
supersedes: []
kit-notes: []
figma: https://www.figma.com/design/QWpZtLfVsUjbc99Lj3JJwJ/Kinetic-Platform---Atomic-Library-of-Elements?node-id=1-15
code: "@kinetic-ui/nav-bars TopBar; reference build https://antonmalashkevych.github.io/kinetic_ux/"
---

# Content tabs

## Anatomy
Top edge of the content area, to the right of the sidebar and Ana panel. A row of open views as tabs; one selected. Kit variants: 1, 2, 3, 4, Many tabs. Many tabs adds an arrow switch at each end.

```
1-4 tabs
+--------------------------------------------------------------+
| [Live Insight Feed] [Command Center x] [Saved 1 x] [Last.. x]|
+--------------------------------------------------------------+
many tabs
+--------------------------------------------------------------+
| < [Tab x] [Tab x] [Tab x] [Tab x] [Ta                      > |
+--------------------------------------------------------------+
```

| Part | Kit component | Tokens | Role / name |
|---|---|---|---|
| Tab list | Navigation bars/Top bar | `shadow-panel-dark` | `tablist` |
| Tab, kit | Tabs/Top bar | `overlay/ghost-pill-bg-interactive`, `text/muted`, `radius/md`; icon close-small | `tab`; `aria-selected` |
| Tab, reference build | Tabs/Top bar | selected `overlay/filter-bar-border-interactive`, `text/primary`; unselected `text/secondary`, hover `state/hover`; `radius/md` | `tab`; `aria-selected` |
| Close | Buttons/Icon button | icon close-small | `button` "Close <tab label>" |
| Count badge | Badges/Status | `state/selected-grey`, `text/muted`, `font-family/mono`, `radius/pill` | text |
| Arrow switch (Many tabs) | Selections/Arrow switches | `overlay/ghost-pill-bg-interactive`, `radius/md`; icon chevron-right | `button` |

## Behavior
- The first tab (Live Insight Feed) has no close control; every other tab has one.
- Exactly one tab is selected.
- A tab MAY carry a count badge after its label.
- Closing a tab removes it from the list; the selected tab is unchanged if it was not the one closed.
- Selected tab in the kit uses the same fill as unselected (`overlay/ghost-pill-bg-interactive`); the reference build differentiates selected with `overlay/filter-bar-border-interactive` and `text/primary`. Reference build is the target.
- Many tabs: the list scrolls with arrow switches at both ends.

## Changelog
- 0.2 2026-09-18: user name removed from Navigation bars/Top bar in Figma (all five variants); tabs left-aligned. User lives in the sidebar footer (nav-sidebar).
- 0.1 2026-09-18: created from Navigation bars/Top bar and reference build.
