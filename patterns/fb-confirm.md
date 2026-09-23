---
id: fb-confirm
name: Confirmation dialog
status: draft
version: 0.1
phase: 1
owner: anton.malashkevych
last-reviewed: 2026-09-23
applies-to: [all]
boundaries: [state-error: result dialogs (Modals/Status Modal), export-share: Download Summary Report and Generate link dialogs, modal-form: dialogs with inputs (Rename Folder)]
related: [fb-toast]
supersedes: []
kit-notes: ["Modals variants contain hidden Stepper and KPI Segments layers inside the Text frame; not exposed as variant properties", "All action buttons in the confirm variants are Buttons/General Type=Primary; no Danger variant is used", "Modals has Interface=Light only as a variant value"]
figma: https://www.figma.com/design/QWpZtLfVsUjbc99Lj3JJwJ/Kinetic-Platform---Atomic-Library-of-Elements?node-id=344-1607
code: ""
---

# Confirmation dialog

## Anatomy
Centered modal that asks the user to confirm before an action proceeds. Kit variant switches: Heading, Description, Additional text, Multi-buttons.

```
+------------------------------------------------+
|                                             x  |
|      Confirm your action before continuing     |
|   Review the selected report settings before   |
|   proceeding. Make sure all filters ...        |
|        This report includes filtered data      |
|                                                |
| [Cancel]  [Export]  [Save View]  [Apply Filters]|
+------------------------------------------------+
```

| Part | Kit component | Tokens | Role / name |
|---|---|---|---|
| Container | Modals | `bg/card`, `radius/xl`, `shadow-modal` | `dialog`, `aria-modal`, labelled by heading |
| Close | Buttons/Icon button/Additional | `overlay/ghost-pill-bg-interactive`, `radius/md`; icon close-small | `button` "Close" |
| Heading (optional) | text | `text/primary`, centered | heading |
| Description | text | `text/primary`, centered | |
| Additional text (optional) | text | `text/muted`, centered | |
| Cancel | Buttons/General Type=Secondary | `bg/surface-subtle`, `border/default`, `radius/input` | `button` |
| Action(s) | Buttons/General Type=Primary | `brand/primary`, `radius/input` | `button`, one per action |

## Behavior
- Cancel is always first (leftmost); actions follow.
- Single action: Cancel + Confirm. Multi-buttons: Cancel + up to three named actions (kit example: Export, Save View, Apply Filters).
- Description is present in every variant; Heading and Additional text are optional.
- Close and Cancel both dismiss without acting.

## Changelog
- 0.1 2026-09-23: created from Modals confirm variants.
