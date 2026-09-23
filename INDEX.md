# VQ8 UX Patterns - Index

Read `AGENTS.md` first. Load a pattern file only when its `applies-to` matches your screen. Status: proposed (informational), draft (follow, report deviations), stable (must follow), deprecated (do not use).

## Loading rules for agents
1. Always load: `AGENTS.md`.
2. For any screen: nav-shell-01, nav-sidebar-01, state-loading-01, state-empty-01, state-error-01, state-permission-01.
3. Add by surface: `applies-to` column below.
4. Add by element: if the screen has a table, load all `table-*`; a detail view, `drill-*`; Ana content, `ana-*` and `insight-card-01`.

## Patterns

| ID | Name | Phase | Status | Applies to | File |
|---|---|---|---|---|---|
| nav-shell-01 | App shell layout | 1 | proposed | shell | patterns/nav-shell-01.md |
| nav-sidebar-01 | Sidebar | 1 | draft | shell | patterns/nav-sidebar-01.md |
| nav-toolbar-01 | Toolbar | 1 | proposed | shell | patterns/nav-toolbar-01.md |
| nav-user-01 | User menu placement and contents | 1 | proposed | shell | patterns/nav-user-01.md |
| nav-ana-01 | Ana panel open, collapsed, closed | 1 | proposed | shell, ana | patterns/nav-ana-01.md |
| nav-tabs-01 | Content tabs | 1 | draft | shell | patterns/nav-tabs-01.md |
| nav-cvbar-01 | CV navigation bar | 1 | proposed | admin | patterns/nav-cvbar-01.md |
| nav-breadcrumb-01 | Breadcrumbs | 1 | draft | analytics, flo, policy-pulse, admin | patterns/nav-breadcrumb-01.md |
| nav-stepper-01 | Stepper | 1 | draft | all | patterns/nav-stepper-01.md |
| nav-client-01 | Client and facility switcher | 1 | proposed | shell | patterns/nav-client-01.md |
| nav-alerts-01 | Alerts entry and list | 1 | proposed | shell | patterns/nav-alerts-01.md |
| nav-help-01 | Help entry point | 1 | proposed | shell | patterns/nav-help-01.md |
| state-loading-01 | Loading states | 1 | proposed | all | patterns/state-loading-01.md |
| state-empty-01 | Empty states | 1 | proposed | all | patterns/state-empty-01.md |
| state-error-01 | Error states | 1 | proposed | all | patterns/state-error-01.md |
| state-permission-01 | No-permission states | 1 | proposed | all | patterns/state-permission-01.md |
| state-stale-01 | Data freshness | 1 | proposed | all | patterns/state-stale-01.md |
| fb-toast-01 | Toasts and confirmations | 1 | proposed | all | patterns/fb-toast-01.md |
| fb-validation-01 | Form validation | 1 | proposed | all | patterns/fb-validation-01.md |
| fb-confirm-01 | Destructive confirmation | 1 | proposed | all | patterns/fb-confirm-01.md |
| theme-01 | Theme switching | 1 | proposed | shell | patterns/theme-01.md |
| drill-in-01 | Drill-in aggregate to detail | 2 | proposed | analytics, flo, policy-pulse | patterns/drill-in-01.md |
| drill-through-01 | Drill-through between apps | 2 | proposed | all | patterns/drill-through-01.md |
| drill-panel-01 | Detail panel vs full page | 2 | proposed | all | patterns/drill-panel-01.md |
| ctx-rightclick-01 | Right-click context menu | 2 | proposed | analytics, flo | patterns/ctx-rightclick-01.md |
| ctx-rowactions-01 | Row hover actions | 2 | proposed | all | patterns/ctx-rowactions-01.md |
| table-01 | Data table baseline | 2 | proposed | all | patterns/table-01.md |
| table-sort-filter-01 | Sorting and filtering | 2 | proposed | all | patterns/table-sort-filter-01.md |
| table-select-bulk-01 | Selection and bulk actions | 2 | proposed | flo, admin | patterns/table-select-bulk-01.md |
| table-paging-01 | Pagination and scroll | 2 | proposed | all | patterns/table-paging-01.md |
| search-01 | Global and in-page search | 2 | proposed | shell, all | patterns/search-01.md |
| filter-global-01 | Global filters | 2 | proposed | analytics, policy-pulse | patterns/filter-global-01.md |
| worklist-01 | Worklist and priority queue | 2 | proposed | flo, denial-copilot | patterns/worklist-01.md |
| insight-card-01 | Ana insight card | 2 | proposed | shell, ana | patterns/insight-card-01.md |
| reco-01 | Recommendation and action cards | 2 | proposed | flo, denial-copilot | patterns/reco-01.md |
| ana-conv-01 | Ana conversation surface | 2 | proposed | ana | patterns/ana-conv-01.md |
| ana-handoff-01 | Ana to view handoff | 2 | proposed | ana, shell | patterns/ana-handoff-01.md |
| save-fav-01 | Favorites, Quick Access, Last Opened | 2 | proposed | shell | patterns/save-fav-01.md |
| export-01 | Export and share | 2 | proposed | all | patterns/export-01.md |
| history-01 | Item history and audit | 2 | proposed | flo, admin | patterns/history-01.md |
| perm-01 | Users, groups, permissions | 2 | proposed | admin | patterns/perm-01.md |
| num-format-01 | Number and date formatting | 3 | proposed | all | patterns/num-format-01.md |
| motion-01 | Motion and transitions | 3 | proposed | all | patterns/motion-01.md |
| kbd-01 | Keyboard navigation | 3 | proposed | all | patterns/kbd-01.md |
| a11y-01 | Accessibility baseline | 3 | proposed | all | patterns/a11y-01.md |
| copy-01 | Microcopy and tone | 3 | proposed | all | patterns/copy-01.md |
| density-01 | Density modes | 3 | proposed | all | patterns/density-01.md |
| tooltip-01 | Tooltips and infoblocks | 3 | proposed | all | patterns/tooltip-01.md |
| badge-01 | Badge semantics | 3 | proposed | all | patterns/badge-01.md |
| chart-interaction-01 | Chart interaction | 3 | proposed | analytics | patterns/chart-interaction-01.md |
| print-01 | Print and PDF | 3 | proposed | analytics | patterns/print-01.md |

## Contribution
Open an issue with the template `pattern-request` or `deviation-report`. New patterns start as `proposed`, get a file from `PATTERN_TEMPLATE.md`, pass the agent test (agent builds a screen from the file alone, output reviewed), then move to `draft` and `stable`. Deprecation is a status change with `supersedes` set on the replacement; files are never deleted.
