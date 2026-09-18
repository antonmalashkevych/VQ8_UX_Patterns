---
id: nav-sidebar-01
name: Sidebar
status: draft
version: 0.2
phase: 1
owner: anton.malashkevych
last-reviewed: 2026-09-18
applies-to: [shell]
kit-components: [Navigation bars/Side bar, Menu items/Side bar/Item card, Inputs/Search field, Tabs/Segments control/Default, Switcher/General, Primitives/Avatars]
related: [nav-shell-01, nav-ana-01, nav-user-01, nav-alerts-01, nav-help-01, save-fav-01]
supersedes: [Navigation bars/Left menu]
figma: https://www.figma.com/design/QWpZtLfVsUjbc99Lj3JJwJ/Kinetic-Platform---Atomic-Library-of-Elements?node-id=1-15
code: "@kinetic-ui/nav-bars SideBar; reference build https://antonmalashkevych.github.io/kinetic_ux/"
---

# Sidebar

## Problem
One global navigation for every screen in the shell, collapsible so it takes minimal width when not in use.

## Use when
- Every screen inside the shell.

## Do not use when
- Actions on the current view: toolbar (nav-toolbar-01).
- Conversation with Ana: Ana panel (nav-ana-01), a separate surface to the right of the sidebar.

## Anatomy
Leftmost column of the shell. Two states: collapsed (icons) and expanded (icons and labels). Parts, top to bottom:

1. Header: brand mark; product name (expanded); toggle.
2. Ana shortcuts, only while the Ana panel is collapsed: New conversation, Conversation history.
3. Finder (expanded): search field; segmented filter Browse, Recent, Most used, Starred; "Pin starred to top" switch.
4. Core items: Command Center, Live Insight Feed, Favorites, Last Opened. Each has a star toggle (expanded).
5. TOOLS group: label (expanded); Denial Resolution Copilot, Patient Access Copilot, Alerts.
6. Footer: Ask Ana, Help, user (avatar; avatar and name when expanded).

```
collapsed          expanded
+----+             +------------------------+
| K  |             | K  Kinetic          <| |
| >  |             | [Search items...     ] |
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

## Tokens
- Container: `bg/surface-deep`, `lines/card`, `radius/card`
- Widths: `TOKEN REQUEST: layout/sidebar-collapsed`, `layout/sidebar-expanded`
- Brand mark: `brand/primary`, `neutral/white`, `radius/control`
- Product name: `text/primary`
- Toggle: `icon/tertiary`, `state/hover`, `radius/control`
- Item default: `text/secondary`, `radius/control`
- Item hover: `state/hover`
- Item active: `state/selected`, `text/primary`
- Group label: `text/decor`
- Search field: `bg/surface-subtle`, `border/default`, `text/placeholder`, `border/active` and `state/focus` on focus
- Segmented filter: selected `bg/surface-muted` `text/primary`; unselected `text/muted`, hover `control/segment-hover`
- Pin switch on: `accent/interactive`, `radius/pill`
- Star on: `brand/primary`
- Avatar: `bg/surface-emphasis`, `text/primary`, `radius/pill`
- Width transition: `TOKEN REQUEST: motion/duration-base`

## Behavior
- MUST be the leftmost column of the shell, full height.
- MUST have two states, collapsed and expanded. Default is collapsed.
- MUST toggle only from the header control. Accessible names: "Expand navigation", "Collapse navigation".
- MUST animate the width change.
- MUST mark the current item with `state/selected` and `aria-current="page"`.
- MUST give each item a `title` equal to its label, so the label is available in the collapsed state.
- Labels MUST be single line and truncate.
- Star toggles MUST use `aria-pressed`; accessible names "Star <label>", "Unstar <label>". Starring does not navigate.
- With "Pin starred to top" on, starred items MUST appear first in the list.
- Search MUST filter items by label. Segmented filter MUST offer Browse, Recent, Most used, Starred; Browse is default.
- Finder MUST NOT appear in the collapsed state.
- Ask Ana MUST focus the Ana input; `/` does the same from outside a text field.
- While the Ana panel is collapsed, the sidebar MUST show New conversation and Conversation history under the header.
- The sidebar MUST NOT contain the Ana conversation.

## Content
- Item labels: product names, title case: "Live Insight Feed", "Denial Resolution Copilot".
- Group label: "TOOLS".
- Footer: "Ask Ana ( / )", "Help", user's first name and last initial.
- Search placeholder: "Search items...".
- Switch label: "Pin starred to top".

## Variants
- Collapsed.
- Expanded.
- Either state with Ana shortcuts, while the Ana panel is collapsed.

## Do / Don't
- Do keep the same items in every app.
- Don't put view actions in the sidebar.
- Don't add a second left navigation.

## Accessibility
- `nav` with `aria-label="Primary navigation"`.
- Current item `aria-current="page"`; stars `aria-pressed`; segmented filter is a `radiogroup`; pin is a `switch`.
- Focus: `state/focus`.

## Rationale
Single collapsible sidebar with icon-only and labeled states, separate from the Ana panel. Replaces the kit's fixed icon-only Left menu.

## Examples
- Figma: Navigation bars/Side bar, Collapse=True and Collapse=False.
- Reference build: https://antonmalashkevych.github.io/kinetic_ux/

## Changelog
- 0.2 2026-09-18: reduced to observed behavior only.
- 0.1 2026-09-18: created.
