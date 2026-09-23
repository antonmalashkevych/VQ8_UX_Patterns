# VQ8 UX Patterns - Index

Read `AGENTS.md` first. Load a pattern file only when its `applies-to` matches your screen. Status: proposed (informational), draft (follow, report deviations), stable (must follow), deprecated (do not use).

## Loading rules for agents
1. Always load: `AGENTS.md`.
2. For any screen: nav-shell, nav-sidebar, state-loading, state-empty, state-error, state-permission.
3. Add by surface: `applies-to` column below.
4. Add by element: if the screen has a table, load all `table-*`; a detail view, `drill-*`; Ana content, `ana-*` and `insight-card`.

## Patterns

| ID | Name | Phase | Status | Applies to | File |
|---|---|---|---|---|---|
| nav-shell | App shell layout | 1 | proposed | shell | patterns/nav-shell.md |
| nav-sidebar | Sidebar | 1 | draft | shell | patterns/nav-sidebar.md |
| nav-toolbar | Toolbar | 1 | proposed | shell | patterns/nav-toolbar.md |
| nav-user-menu | User menu placement and contents | 1 | proposed | shell | patterns/nav-user-menu.md |
| nav-ana-panel | Ana panel | 1 | draft | shell, ana | patterns/nav-ana-panel.md |
| nav-content-tabs | Content tabs | 1 | draft | shell | patterns/nav-content-tabs.md |
| nav-cvbar | CV navigation bar | 1 | proposed | admin | patterns/nav-cvbar.md |
| nav-breadcrumb | Breadcrumbs | 1 | draft | analytics, flo, policy-pulse, admin | patterns/nav-breadcrumb.md |
| nav-stepper | Stepper | 1 | draft | all | patterns/nav-stepper.md |
| nav-reports-tree | Reports tree | 1 | draft | analytics | patterns/nav-reports-tree.md |
| nav-alerts | Alerts panel | 1 | draft | shell | patterns/nav-alerts.md |
| nav-help | Help entry point | 1 | proposed | shell | patterns/nav-help.md |
| state-loading | Loading states | 1 | proposed | all | patterns/state-loading.md |
| state-empty | Empty states | 1 | proposed | all | patterns/state-empty.md |
| state-error | Error states | 1 | proposed | all | patterns/state-error.md |
| state-permission | No-permission states | 1 | proposed | all | patterns/state-permission.md |
| state-stale | Data freshness | 1 | proposed | all | patterns/state-stale.md |
| fb-toast | Toasts and confirmations | 1 | proposed | all | patterns/fb-toast.md |
| fb-validation | Form validation | 1 | proposed | all | patterns/fb-validation.md |
| fb-confirm | Destructive confirmation | 1 | proposed | all | patterns/fb-confirm.md |
| theme-switch | Theme switching | 1 | proposed | shell | patterns/theme-switch.md |
| drill-in | Drill-in aggregate to detail | 2 | proposed | analytics, flo, policy-pulse | patterns/drill-in.md |
| drill-through | Drill-through between apps | 2 | proposed | all | patterns/drill-through.md |
| drill-panel | Detail panel vs full page | 2 | proposed | all | patterns/drill-panel.md |
| ctx-rightclick | Right-click context menu | 2 | proposed | analytics, flo | patterns/ctx-rightclick.md |
| ctx-rowactions | Row hover actions | 2 | proposed | all | patterns/ctx-rowactions.md |
| table-base | Data table baseline | 2 | proposed | all | patterns/table-base.md |
| table-sort-filter | Sorting and filtering | 2 | proposed | all | patterns/table-sort-filter.md |
| table-select-bulk | Selection and bulk actions | 2 | proposed | flo, admin | patterns/table-select-bulk.md |
| table-paging | Pagination and scroll | 2 | proposed | all | patterns/table-paging.md |
| search | Global and in-page search | 2 | proposed | shell, all | patterns/search.md |
| filter-global | Global filters | 2 | proposed | analytics, policy-pulse | patterns/filter-global.md |
| worklist | Worklist and priority queue | 2 | proposed | flo, denial-copilot | patterns/worklist.md |
| insight-card | Ana insight card | 2 | proposed | shell, ana | patterns/insight-card.md |
| recommendation-card | Recommendation and action cards | 2 | proposed | flo, denial-copilot | patterns/recommendation-card.md |
| ana-conv | Ana conversation surface | 2 | proposed | ana | patterns/ana-conv.md |
| ana-handoff | Ana to view handoff | 2 | proposed | ana, shell | patterns/ana-handoff.md |
| save-favorites | Favorites, Quick Access, Last Opened | 2 | proposed | shell | patterns/save-favorites.md |
| export-share | Export and share | 2 | proposed | all | patterns/export-share.md |
| item-history | Item history and audit | 2 | proposed | flo, admin | patterns/item-history.md |
| permissions-ui | Users, groups, permissions | 2 | proposed | admin | patterns/permissions-ui.md |
| num-format | Number and date formatting | 3 | proposed | all | patterns/num-format.md |
| motion | Motion and transitions | 3 | proposed | all | patterns/motion.md |
| keyboard-nav | Keyboard navigation | 3 | proposed | all | patterns/keyboard-nav.md |
| accessibility | Accessibility baseline | 3 | proposed | all | patterns/accessibility.md |
| microcopy | Microcopy and tone | 3 | proposed | all | patterns/microcopy.md |
| density-modes | Density modes | 3 | proposed | all | patterns/density-modes.md |
| tooltip | Tooltips and infoblocks | 3 | proposed | all | patterns/tooltip.md |
| badge-semantics | Badge semantics | 3 | proposed | all | patterns/badge-semantics.md |
| chart-interaction | Chart interaction | 3 | proposed | analytics | patterns/chart-interaction.md |
| print-layout | Print and PDF | 3 | proposed | analytics | patterns/print-layout.md |

## Contribution
Open an issue with the template `pattern-request` or `deviation-report`. New patterns start as `proposed`, get a file from `PATTERN_TEMPLATE.md`, pass the agent test (agent builds a screen from the file alone, output reviewed), then move to `draft` and `stable`. Deprecation is a status change with `supersedes` set on the replacement; files are never deleted.
