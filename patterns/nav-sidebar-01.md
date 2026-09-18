---
id: nav-sidebar-01
name: Sidebar
status: draft
version: 0.1
phase: 1
owner: anton.malashkevych
last-reviewed: 2026-09-18
applies-to: [shell]
kit-components: [Navigation bars/Side bar, Menu items/Side bar/Item card, Inputs/Search field, Tabs/Segments control/Default, Switcher/General, Primitives/Avatars, Tooltip]
related: [nav-shell-01, nav-ana-01, nav-user-01, nav-alerts-01, nav-help-01, save-fav-01, search-01]
supersedes: [Navigation bars/Left menu]
figma: https://www.figma.com/design/QWpZtLfVsUjbc99Lj3JJwJ/Kinetic-Platform---Atomic-Library-of-Elements?node-id=1-15
code: "@kinetic-ui/nav-bars SideBar; reference build https://antonmalashkevych.github.io/kinetic_ux/"
---

# Sidebar

## Problem
Users move between the Command Center, feeds, saved views, and tools many times an hour. Without one fixed place for destinations, each app invents its own navigation, users lose orientation when drilling across apps, and screen width is wasted on labels the user already knows. The sidebar is the single global navigation of the shell: always present, always in the same place, collapsible so it costs almost nothing when not needed.

## Use when
- Any screen rendered inside the shell. The sidebar is not optional.

## Do not use when
- Navigating sections inside a single app or admin area with many subsections. Use in-page tabs (nav-tabs-01) or a content-area section list; never a second sidebar.
- Actions on the current view (export, reload, favorite this view). Those go in the toolbar (nav-toolbar-01).
- Conversing with Ana. That is the Ana panel (nav-ana-01), a separate surface to the right of the sidebar.

## Anatomy
The sidebar is the leftmost column of the shell. It has two states, collapsed (icons only) and expanded (icons with labels plus finder controls). Parts, top to bottom:

1. Header: brand mark; product name (expanded only); collapse or expand toggle.
2. Ana shortcuts (only when the Ana panel is collapsed): New conversation, Conversation history.
3. Finder (expanded only): search field; segmented filter Browse, Recent, Most used, Starred; "Pin starred to top" switch.
4. Destinations: items the user navigates to, grouped. Starred items sit at the top when pinning is on. Each item shows an icon, a label (expanded), and a star toggle (expanded, on hover or when starred).
5. Group label (expanded only): caps text naming the group below it, such as TOOLS.
6. Footer, pinned to the bottom: Ask Ana, Help, user (avatar; avatar with name when expanded). The user item opens the user menu (nav-user-01).

```
collapsed              expanded
+----+                 +------------------------+
| K  |                 | K  Kinetic          <| |
| >  |                 | [search items        ] |
|----|                 | Browse Recent Most Star|
| +  |  (Ana shortcuts | Pin starred to top  (o)|
| h  |   when Ana      |------------------------|
|----|   panel closed) | * Command Center     * |
| o  |                 | o Live Insight Feed  * |
| o  |                 | o Favorites          * |
| o  |                 | o Last Opened        * |
| o  |                 | TOOLS                  |
|    |                 | o Denial Resolution    |
|    |                 | o Patient Access       |
|    |                 | o Alerts               |
|    |                 |                        |
| a  |                 | a Ask Ana        ( / ) |
| ?  |                 | ? Help                 |
| AM |                 | AM Anton M.            |
+----+                 +------------------------+
```

## Tokens
- Container: `bg/surface-deep`, `lines/card`, `radius/card`, `layout/sidebar-collapsed`, `layout/sidebar-expanded`, `layout/shell-gutter`
- Header: `brand/primary` (brand mark), `neutral/white` (mark glyph), `text/primary` (product name), `radius/control`
- Item, default: `text/secondary`, `icon/secondary`, `radius/control`, `font-size/s`
- Item, hover: `state/hover`
- Item, active: `state/selected`, `text/primary`, `icon/primary`
- Item, focus: `state/focus`, `border/active`
- Group label: `text/decor`, `font-size/cap`, `font-weight/semibold`
- Search field: `bg/surface-subtle`, `border/default`, `text/placeholder`
- Segmented filter: `bg/surface-muted` (selected segment), `text/muted` (unselected), `control/segment-hover`, `font-size/meta`
- Pin switch: `accent/interactive` (on), `control/track` (off), `radius/pill`
- Star: `brand/primary` (starred), `icon/tertiary` (unstarred)
- Avatar: `bg/surface-emphasis`, `text/primary`, `radius/pill`
- Motion: `motion/duration-base`, `easing/standard` (width transition)
- `TOKEN REQUEST: layout/sidebar-collapsed`, `layout/sidebar-expanded`, `motion/duration-base`, `easing/standard`

## Behavior
Placement
- MUST be the leftmost column of the shell and span full shell height, inset by `layout/shell-gutter` (nav-shell-01).
- MUST be the only global navigation. No top bar, no second sidebar.
- MUST render in every app and every route inside the shell with the same items and order; app switching never changes it.

States
- MUST have exactly two states: collapsed at `layout/sidebar-collapsed` (icons only) and expanded at `layout/sidebar-expanded` (icons with labels and finder).
- MUST default to collapsed on first use.
- SHOULD persist the state per user across sessions. Collapsing is not a per-page choice.
- MUST animate width with `motion/duration-base`; content area reflows, nothing overlaps it.
- MUST toggle from the header control only. Clicking an item never changes the state.

Items
- MUST show each destination as a single-line label with an icon. Labels truncate with an ellipsis; they never wrap.
- MUST mark the current destination with `state/selected` and `aria-current="page"`. Exactly one item is current.
- MUST show the label as a tooltip on hover and focus when collapsed (Tooltip). In collapsed state the icon is the only visible identity, so every icon MUST be unique within the sidebar.
- MUST show a star toggle on each destination in the expanded state. Starred is `brand/primary`. Starring never navigates.
- MAY show a count badge on Alerts (nav-alerts-01). No other item carries a badge.
- MUST NOT place actions in the sidebar. New conversation and Conversation history are the one exception, and only while the Ana panel is collapsed.

Groups
- MUST order groups: Command Center and core views, then TOOLS, then footer. Groups have a caps label in the expanded state and a divider gap in the collapsed state.
- Starred items with "Pin starred to top" on MUST appear as the first group, in the order starred, and disappear from their home group while pinned.

Finder (expanded only)
- Search MUST filter destinations by label as the user types, across all groups, and show a one-line empty result inside the list when nothing matches (state-empty-01).
- Segmented filter MUST offer Browse (all, grouped), Recent, Most used, Starred. Browse is the default. Selection persists with the sidebar state.
- Finder MUST NOT appear in the collapsed state.

Ana relation
- The sidebar MUST NOT contain the Ana conversation. Ana is a separate panel to the right of the sidebar (nav-ana-01).
- When the Ana panel is expanded, the sidebar shows only the Ask Ana footer item. When the Ana panel is collapsed, the sidebar additionally shows New conversation and Conversation history under the header.
- Ask Ana MUST focus the Ana input, expanding the panel if collapsed. Keyboard: `/` from anywhere outside a text field does the same.

Keyboard
- Tab order: toggle, Ana shortcuts, search, filter, items top to bottom, footer. Arrow keys move between items. Enter or Space activates. Escape from the search field clears it, then returns focus to the toggle.

Responsive
- Below the narrow breakpoint the sidebar MUST be collapsed and MUST NOT expand inline; the expanded state opens as an overlay over content and closes on selection or Escape.

Loading and permission
- Items the user has no permission for MUST NOT render. The sidebar never shows disabled destinations.
- Sidebar renders synchronously with the shell; it has no loading state of its own. Counts (Alerts) load after and appear without shifting layout.

## Content
- Labels are the product names of the destinations, title case, no verbs: "Live Insight Feed", "Denial Resolution Copilot".
- Group labels are one word in caps: TOOLS.
- Footer: "Ask Ana", "Help", user's first name and last initial.
- Search placeholder: "Search items...".
- Toggle accessible names: "Expand navigation", "Collapse navigation". Star: "Star <label>", "Unstar <label>".
- Ask Ana shows its shortcut in the label: "Ask Ana ( / )".

## Variants
- Collapsed: default. Icons, tooltips, no finder, footer as icons.
- Expanded: labels, finder, star toggles, footer with name.
- Ana panel collapsed: either state plus New conversation and Conversation history under the header.
- Overlay (narrow viewport): expanded state drawn over content instead of beside it.

## Do / Don't
- Do keep the item set identical in every app.
- Do put every destination in the sidebar, even if reachable from elsewhere.
- Don't add an app-level left navigation inside the content area.
- Don't put export, reload, or view actions in the sidebar; use the toolbar.
- Don't badge anything except Alerts.
- Don't use Menu items/Side bar/Item card with a description line in the global sidebar; that variant is for section lists inside admin areas rendered in the content area.

## Accessibility
- Container is `nav` with `aria-label="Primary navigation"`.
- Toggle has an accessible name that states the resulting action.
- Current item carries `aria-current="page"`. Star toggles are `aria-pressed`.
- Collapsed icons expose their label via tooltip and accessible name; icon-only controls never rely on the icon alone.
- Focus ring uses `state/focus` and is visible on `bg/surface-deep`.
- Reduced motion preference disables the width transition.

## Rationale
One collapsible sidebar replaces the two-level model in the kit (a fixed icon-only Left menu plus an in-app Side bar) because users switch between Command Center, feeds, and copilots constantly and a second level of navigation was where inconsistency across VQ8 apps started. The collapsed default protects horizontal space for dense tables and the Ana panel; labels are one click away when learning the product. Ana lives in its own panel rather than in the sidebar because a conversation needs width and persistence that a navigation column cannot give, while the sidebar keeps a shortcut so Ana is reachable from any state. Starring and the finder live in the sidebar because the item set will grow with each copilot and users should be able to shape their own top group without an admin.

## Examples
- Figma: Navigation bars/Side bar, variants Collapse=True and Collapse=False, page "Navigation bars" (link in frontmatter).
- Reference build: https://antonmalashkevych.github.io/kinetic_ux/ (collapsed default; toggle in header; Ana panel collapse to see Ana shortcuts).

## Changelog
- 0.1 2026-09-18: created from Kinetic Side bar component and kinetic_ux reference build. Folds in item states formerly planned as nav-sidebar-02.
