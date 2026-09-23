---
id: fb-status-dialog
name: Status dialog
status: draft
version: 0.1
phase: 1
owner: anton.malashkevych
last-reviewed: 2026-09-23
applies-to: [all]
boundaries: [fb-confirm: asking before an action, fb-toast: transient result notices, state-error: inline and banner errors]
related: [fb-confirm, state-error]
supersedes: []
kit-notes: ["In Modals/Status Modal State=Error the Try Again button instance is Buttons/General State=Disabled while rendering as enabled; check the variant property", "Success icon is the unnamespaced component ready 2"]
figma: https://www.figma.com/design/QWpZtLfVsUjbc99Lj3JJwJ/Kinetic-Platform---Atomic-Library-of-Elements?node-id=344-1607
code: ""
---

# Status dialog

## Anatomy
Centered modal reporting the result of an operation. Two states: Success, Error.

```
success                              error
+----------------------------+       +----------------------------------+
| (v) File uploaded       x  |       | (!) Upload error              x  |
|     Your file was success..|       |     Something went wrong, ...     |
|                   [Close]  |       |            [Close]  [Try Again]  |
+----------------------------+       +----------------------------------+
```

| Part | Kit component | Tokens | Role / name |
|---|---|---|---|
| Container | Modals/Status Modal | `bg/card`, `radius/xl`, `shadow-modal` | `alertdialog`, labelled by title |
| Status icon, Success | ready 2 | `neutral/white` glyph on success fill | decorative |
| Status icon, Error | text "!" in circle | `semantic/error` fill, `neutral/white` glyph | decorative |
| Title | text | `text/primary` | heading |
| Message | text | `text/primary` | |
| Close (corner) | Buttons/Icon button/Additional | `overlay/ghost-pill-bg-interactive`, `radius/md`; icon close-small | `button` "Close" |
| Close (footer) | Buttons/General Type=Secondary | `bg/surface-subtle`, `border/default`, `radius/input` | `button` |
| Try Again (Error) | Buttons/General Type=Primary | `brand/primary`, `radius/input` | `button` |

## Behavior
- Success has one footer action, Close.
- Error has two: Close, then Try Again as the primary.
- Icon and title sit on one line, message beneath, left-aligned; footer actions right-aligned.

## Changelog
- 0.1 2026-09-23: created from Modals/Status Modal (Success, Error).
