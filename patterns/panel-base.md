---
id: panel-base
name: Panel
status: draft
version: 0.1
phase: 1
owner: anton.malashkevych
last-reviewed: 2026-09-23
applies-to: [all]
boundaries: [nav-ana-panel: the Ana panel specifics, nav-alerts: Alerts panel content, nav-reports-tree: Reports panel content, fb-confirm: modal dialogs]
related: [nav-shell, item-history, worklist, recommendation-card]
supersedes: []
kit-notes: ["Panels/Item History and Panels/Chat lack the shadow-panel-dark effect the other seven panels carry", "Panels/Chat root fill is bg/page while all other panels are bg/card", "Panels come in two widths; TOKEN REQUEST: layout/panel-narrow, layout/panel-wide", "Every Panels/* set carries a Dark/Light variant property with only the False value"]
figma: https://www.figma.com/design/QWpZtLfVsUjbc99Lj3JJwJ/Kinetic-Platform---Atomic-Library-of-Elements?node-id=13282-181812
code: ""
---

# Panel

## Anatomy
Vertical surface that opens inside the shell beside the content, full shell height. Shared by Panels/Alerts, Reports, Conversation, Flo, Flo Rules, Action, Worklist Option, Item History, Chat. Header with title and close; body specific to the panel.

```
+------------------------+
| Title        [opt]  x  |
|------------------------|
| body                   |
|                        |
+------------------------+
```

| Part | Kit component | Tokens | Role / name |
|---|---|---|---|
| Container | Panels/* | `bg/card`, `radius/lg`, `shadow-panel-dark`; width `layout/panel-narrow` (Alerts, Reports, Conversation, Flo Rules) or `layout/panel-wide` (Flo, Action, Worklist Option, Item History, Chat) | `region` or `dialog` named by title |
| Header | Headers/Panels (Headers/Conversations panel, Headers/Item history, Headers/Chat for those three) | title `text/primary`, `font-size/md`, `font-weight/semibold`; divider below | heading |
| Header optional control | varies | Conversations: mail-off toggle; Item History: Switcher/General "New-Old / Old-New"; Chat: drag handle, subtitle | |
| Close | Buttons/Icon button/Additional | `overlay/ghost-pill-bg-interactive`, `radius/md`; icon close-small | `button` "Close" |
| Body | panel-specific | | |

## Behavior
- Close is always the last control in the header, top right.
- Header title is the panel name; Chat adds a subtitle line under the title.
- Body content and its states belong to the specific panel pattern.

## Changelog
- 0.1 2026-09-23: created from the nine Panels/* component sets.
