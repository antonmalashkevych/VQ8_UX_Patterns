---
id: <area>-<specific-name>       # stable, never reused. e.g. nav-user-menu
name: <Human name>
status: proposed | draft | stable | deprecated
version: 0.1
phase: 1 | 2 | 3
owner: anton.malashkevych
last-reviewed: YYYY-MM-DD
applies-to: [shell, analytics, flo, policy-pulse, denial-copilot, patient-access-copilot, ana, admin]
boundaries: [nav-toolbar: view actions, nav-ana-panel: Ana conversation]   # what this pattern is not; pattern ID and one phrase
related: [nav-shell]
supersedes: []                   # pattern IDs this replaces
kit-notes: []                    # KIT REQUEST or TOKEN REQUEST lines
figma: <url or empty>
code: <path or package export or empty>
---

# <Human name>

## Anatomy
One sentence on placement. Diagram showing states. Then a parts table: every part once, with its kit component, tokens by state, and role or accessible name. Full Figma component paths. No literal values; a missing token is `TOKEN REQUEST: <name>`.

```
+---------+-------------------------------+
| sidebar | content                       |
+---------+-------------------------------+
```

| Part | Kit component | Tokens | Role / name |
|---|---|---|---|
| ... | ... | default: ...; hover: ...; active: ... | ... |

## Behavior
Rules with RFC 2119 keywords, one per line, only what has been observed in the kit or the reference build. Do not repeat what the table already states.

- MUST ...
- MUST NOT ...

## Changelog
- 0.1 YYYY-MM-DD: created from <source>.
