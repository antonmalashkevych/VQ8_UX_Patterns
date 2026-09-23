---
id: nav-stepper-01
name: Stepper
status: draft
version: 0.1
phase: 1
owner: anton.malashkevych
last-reviewed: 2026-09-23
applies-to: [all]
boundaries: [nav-tabs-01: open views, nav-breadcrumb-01: location in a hierarchy]
related: [fb-validation-01]
supersedes: []
kit-notes: ["Not present in the reference build; documented from the kit only", "KIT REQUEST: variant Step=3, # of steps=5 contains a stray ellipse (Oval Copy 7, text/primary) outside the atom instances"]
figma: https://www.figma.com/design/QWpZtLfVsUjbc99Lj3JJwJ/Kinetic-Platform---Atomic-Library-of-Elements?node-id=13331-185125
code: ""
---

# Stepper

## Anatomy
Horizontal row of step dots joined by connector lines, one dot per step, no labels. Kit variants: Step (1 to 5) by number of steps (2 to 5), 14 combinations. Atom states: Current, Interacted, Done, Inactive.

```
step 3 of 5
(v)---(v)---(o)---( )---( )
done  done  current inactive inactive
```

| Part | Kit component | Tokens | Role / name |
|---|---|---|---|
| Container | Navigation/Stepper | horizontal auto-layout | `list`, "Step <n> of <total>" |
| Step, Current | Navigation/Atom/Stepper | outer ring `accent/interactive` on `bg/page`; inner dot `accent/interactive` | `aria-current="step"` |
| Step, Interacted | Navigation/Atom/Stepper | ring `accent/interactive` on `bg/page`, no inner dot | |
| Step, Done | Navigation/Atom/Stepper | fill `accent/interactive`; check mark `bg/page` | |
| Step, Inactive | Navigation/Atom/Stepper | ring `border/active` at reduced opacity on `bg/page` | |
| Connector | Foundations/Divider/Horizontal | Default between done steps; Muted before inactive steps | decorative |

## Behavior
- Exactly one step is Current. Steps before it are Done or Interacted; steps after it are Inactive.
- Interacted marks a step the user visited but did not complete.
- Dots carry no labels; the step name lives in the content the stepper heads.

## Changelog
- 0.1 2026-09-23: created from Navigation/Stepper and Navigation/Atom/Stepper.
