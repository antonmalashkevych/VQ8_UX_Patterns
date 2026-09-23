---
id: nav-ana-panel
name: Ana panel
status: draft
version: 0.1
phase: 1
owner: anton.malashkevych
last-reviewed: 2026-09-23
applies-to: [shell, ana]
boundaries: [nav-sidebar: Ask Ana item and Ana shortcuts, ana-conv: message content and response types, ana-handoff: linking answers to views]
related: [nav-shell, insight-card]
supersedes: []
kit-notes: ["Panels/Conversation (List, Conversation, Settings) is a team conversations panel with participants and email settings, not Ana; do not use it for this pattern", "Kit Panels/Chat has header, drag handle, and close; the reference build has header, history, New conversation, collapse, and a resize handle. Reference build is the target", "TOKEN REQUEST: layout/panel-ana-expanded, layout/panel-ana-collapsed, layout/panel-ana-min"]
figma: https://www.figma.com/design/QWpZtLfVsUjbc99Lj3JJwJ/Kinetic-Platform---Atomic-Library-of-Elements?node-id=13282-181812
code: "reference build https://antonmalashkevych.github.io/kinetic_ux/"
---

# Ana panel

## Anatomy
Column between the sidebar and the content area. Two states: expanded (header, scrolling body, footer) and collapsed (narrow strip). Body has three views: home, conversation, history.

```
expanded                              collapsed
+----------------------------------+  +---+
| (A) Ana        (h) [+ New conv] <|  | A |
|----------------------------------|  | . |
| Good morning, Anton              |  | A |
| 15 facilities · claims thru ...  |  | s |
| KEY CHANGES TODAY                |  | k |
| [tile] [tile] [tile]             |  |   |
| ACTIVE ALERTS                    |  | A |
| [alert] [alert] [alert]          |  | n |
| START WITH A QUESTION            |  | a |
| [question] [question] ...        |  | / |
|----------------------------------|  +---+
| [scope chip x]  press / to focus |
| [Ask about your data...   ] [>]  |
+----------------------------------+|<- resize handle
```

| Part | Kit component | Tokens | Role / name |
|---|---|---|---|
| Container, expanded | Panels/Chat | `bg/card`, `lines/card`, `radius/card`; width `layout/panel-ana-expanded`, min `layout/panel-ana-min` | `region` "Ana conversation panel" |
| Container, collapsed | strip | `bg/card`, `lines/card`, `radius/card`; hover `border/active`; width `layout/panel-ana-collapsed`; Ana avatar and vertical label | `button` "Open Ana - ask about your data (or press /)" |
| Header | Headers/Chat | bottom border `lines/card`; title `text/primary`, `font-weight/semibold`; Ana avatar Icon/Ana/Rounded chat icons | heading "Ana" |
| Header actions | Buttons/Icon button; Buttons/General primary | icon buttons `icon/tertiary`, hover `state/hover`; New conversation `brand/primary`, `neutral/white` | "Ana home" (conversation view only), "Conversation history", "New conversation", "Collapse Ana panel" |
| Body | scroll region | | |
| Home: greeting | text | `text/primary`, `font-weight/semibold`; subline `text/secondary` | heading "Good morning, <first name>" |
| Home: section label | text | `text/decor`, caps | "KEY CHANGES TODAY", "ACTIVE ALERTS", "START WITH A QUESTION" |
| Home: KPI tile | Cards/Flo cards | metric `font-family/mono`; change `semantic/success` or `semantic/error`; sparkline | `img` "<metric> 8-period trend" |
| Home: alert row | button | `bg/surface-subtle`, `lines/hairline`, `radius/control`, `text/secondary`; hover `border/active`; icon bell | `button` |
| Home: question chip | button | `overlay/ghost-pill-bg-interactive`, `accent/interactive-soft`, `radius/control`; hover `state/selected-subtle` | `button` |
| Conversation: messages | Conversation item/Chat/Ana response, Conversation item/Chat/User response | see ana-conv | |
| Conversation: follow-ups | [Review] Ana/Buttons | as question chip | `button` |
| History: list | Conversation item/Molecules/Conversations list items | title `text/primary`; meta `text/muted`; section label "RECENT CONVERSATIONS" | `button` per conversation |
| Footer: scope chip | Badges/Chips | breadcrumb-style label "Command Center › Denial Rate"; clear icon | `button` "Clear metric scope" |
| Footer: hint | text | `text/muted`; "press / to focus" | |
| Footer: input | Inputs/Chat | `bg/surface-subtle`, `border/default`, `text/placeholder`; focus `border/active` | textbox "Ask Ana about your data", placeholder "Ask about your data..." |
| Footer: send | Buttons/General primary | `brand/primary`, `neutral/white`; icon send | `button` "Send" |
| Resize handle | separator | full height on the right edge; cursor col-resize | `separator` "Resize Ana panel", vertical, `aria-valuenow` = width |

## Behavior
- Default state is expanded with the home view.
- Collapse hides the body and footer and shows the strip; New conversation and Conversation history move to the sidebar (nav-sidebar).
- Clicking the strip, the sidebar Ask Ana item, or pressing `/` outside a text field expands the panel and focuses the input.
- Sending a message switches the body to the conversation view; the header gains "Ana home".
- Conversation history replaces the body with the list; selecting an entry opens that conversation.
- New conversation returns to an empty conversation.
- A metric scope, once set by a question or by a view, shows as a chip in the footer until cleared.
- Width is user-resizable by dragging the handle, not below `layout/panel-ana-min`.

## Changelog
- 0.1 2026-09-23: created from reference build and kit Panels/Chat, Headers/Chat, Inputs/Chat, Conversation item.
