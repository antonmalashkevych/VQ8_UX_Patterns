---
id: <area>-<name>-<nn>          # stable, never reused. e.g. nav-user-01
name: <Human name>
status: proposed | draft | stable | deprecated
version: 0.1
phase: 1 | 2 | 3
owner: anton.malashkevych
last-reviewed: YYYY-MM-DD
applies-to: [shell, analytics, flo, policy-pulse, denial-copilot, patient-access-copilot, ana, admin]
kit-components: [Navigation bars/Side bar, Menu items/Profile menu]   # exact Kinetic names; MISSING: <name> for gaps
related: [nav-shell-01, nav-sidebar-01]
supersedes: []                   # for deprecations
figma: <url or empty>
code: <path or package export or empty>
---

# <Human name>

## Problem
One paragraph. What the user is trying to do and what goes wrong without a shared rule.

## Use when
- Condition.

## Do not use when
- Condition, and what to use instead (pattern ID).

## Anatomy
Text description of the parts, top to bottom or left to right. Name each part; reuse the names below. ASCII sketch if layout matters:

```
+---------+-------------------------------+
| sidebar | content                       |
|         |                               |
+---------+-------------------------------+
```

## Tokens
Every dimension, color, radius, shadow, type size, weight, border, and duration this pattern depends on, as Kinetic variable names. No literal values anywhere in this file. Missing token: `TOKEN REQUEST: <proposed name>`.

- `layout/...`
- `bg/...`, `text/...`
- `motion/...`

## Behavior
Rules with RFC 2119 keywords. One rule per line. Cover: default state, interactions (click, hover, keyboard, right-click), states (loading, empty, error, no-permission, stale), responsive behavior, persistence. Reference tokens by name, never values.

- MUST ...
- MUST NOT ...
- SHOULD ...
- MAY ...

## Content
Copy rules: labels, casing, max length, placeholder text, error wording.

## Variants
Name each variant and the condition that selects it.

## Do / Don't
- Do: ...
- Don't: ...

## Accessibility
Focus order, aria labels, contrast notes, keyboard equivalents.

## Rationale
Why this decision, what was rejected and why. Two to five sentences. This section prevents relitigation.

## Examples
Links to Figma frames and code references. Nothing load-bearing lives only in an image.

## Changelog
- 0.1 YYYY-MM-DD: created.
