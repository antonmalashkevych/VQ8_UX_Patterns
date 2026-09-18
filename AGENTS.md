# AGENTS.md - VQ8 UX Patterns Library

Version 0.1 (Phase 0 draft). Owner: Anton Malashkevych, Senior Design Manager. Status of every fact below: `[verified]` = confirmed from a source, `[draft]` = needs owner confirmation.

This file is the entry point for any AI agent or human generating, reviewing, or implementing VisiQuate product UI. Read it first. Then load only the pattern files you need from `patterns/` via `INDEX.md`.

---

## 1. How to use this library

1. Read this file fully. It carries business context, the product map, the UI kit boundary, and the rules.
2. Open `INDEX.md`. Load only the patterns whose `applies-to` matches the screen you are working on. Do not load everything.
3. Compose the screen from Kinetic UI kit components (section 5) arranged according to the loaded patterns (section 6). Never redefine a kit component inside a pattern.
4. In your output, cite pattern IDs you applied (`nav-shell-01`, `state-empty-01`). If two patterns conflict, or the brief requires something no pattern covers, stop and report the gap. Do not invent a resolution silently.
5. Keywords MUST, MUST NOT, SHOULD, MAY follow RFC 2119. MUST rules are checkable; a screen violating one is non-compliant.
6. Pattern status governs use: `stable` MUST be followed, `draft` SHOULD be followed and deviations reported, `proposed` is informational, `deprecated` MUST NOT be used for new work.

---

## 2. VisiQuate business context

### 2.1 What the company does
VisiQuate provides AI-powered revenue cycle management (RCM) analytics and workflow software for US healthcare providers: hospital systems, physician groups, specialty providers, and healthcare services companies. `[verified]`

The revenue cycle is the sequence from patient scheduling and registration, through coding and claim submission to payers (insurers, Medicare, Medicaid), to payment, denial, appeal, and patient self-pay collection. VisiQuate ingests data from these disconnected systems into one platform and turns it into insights, predictions, and prioritized work. `[verified]`

### 2.2 Business goals the product serves
- Prevent claim denials before submission by predicting denial risk and detecting payer policy changes early. `[verified]`
- Recover revenue already lost or at risk: denied claims, underpayments, late charges, credit balances, "black hole" accounts with no payer activity. `[verified]`
- Prioritize work so staff act on the highest-value accounts first (Flo prioritization model, Prioritization Assistant, Bundling Manager for collective appeals and escalations). `[verified]`
- Recommend next actions for collections and follow-up (Recommendation Expert agent, recommendation engine components in the kit). `[verified]`
- Give leadership forecasting and control: cash flow forecasting, CFO Reserves and Forecasting Suite, A/R days, aging buckets, payer performance benchmarks. `[verified]`
- Hold payers accountable: track payer behavior against benchmarks, escalate with evidence, tie escalations to recoveries (Payer Action Center). `[verified]`
- Commercial promise: 3-5X return on analytics within 12 months. `[verified]`

### 2.3 Product surfaces
From visiquate.com and the Kinetic reference build (https://antonmalashkevych.github.io/kinetic_ux/). Sidebar placement follows the reference build. `[verified from reference build]`

| Surface | What it is | Sidebar placement |
|---|---|---|
| Ana | AI intelligence layer: nine agents (Account Navigator, Anomaly Detector, Conversational Analytics Assistant, KPI Insights Coach, Recommendation Expert, Bundling Manager, Workflow Optimizer, Prioritization Assistant, plus one more). Conversational panel, insight feed, suggested dashboards. | Own panel between sidebar and content, expanded or collapsed (`layout/panel-ana-expanded`, `layout/panel-ana-collapsed`); sidebar footer item Ask Ana; New conversation and Conversation history appear in the sidebar only while the panel is collapsed |
| Analytics | Analytics Suite: Denials Management, Revenue Management, Patient Access, Coding Audit, Workforce Performance, Vendor Performance; Performance Power Packs (E&M Sonar, Late Charge, Self-Pay, Credit Balance, Charge Reconciliation) | Not in reference build sidebar `[draft]` |
| FLO | Workflow and prioritization (Full Score - Flo); Flo grid, Flo rules, worklists | Not in reference build sidebar `[draft]` |
| Policy Pulse | Payer policy change monitoring, impact scoring, scenario modeling | Not in reference build sidebar `[draft]` |
| Denial Resolution Copilot | AI-assisted denial workflow app | Sidebar, TOOLS group |
| Patient Access Copilot | AI-assisted front-end (registration, authorization, eligibility) app | Sidebar, TOOLS group |
| Payer Action Center | Track, escalate, recover against payers | Not in reference build sidebar `[draft]` |
| Command Center, Live Insight Feed, Favorites, Last Opened | Home views: insight feed, favorites, recently opened items | Sidebar, core group; any item can be starred and pinned to top |
| Alerts | Alert list; the only badged item | Sidebar, TOOLS group |
| Ask Ana, Help, User | Ask Ana focuses the Ana input (shortcut `/`); Help; user opens the user menu | Sidebar footer |

### 2.4 Users
Primary: revenue cycle directors and managers, denials and appeals specialists, billing and coding staff, patient access staff, payer relations, compliance. Secondary: CFO and executive leadership consuming summaries and forecasts. Users work in dense data all day, often across several payers and facilities, and are measured on dollars recovered, A/R days, and denial rate. `[verified from marketing, roles need confirmation against actual personas]`

### 2.5 Constraints that shape UX
- Data density is a feature. Tables, KPIs, and financial numbers dominate. Numerals use `font-family/mono` for alignment and digit clarity. `[verified from Kinetic typography page]`
- Accuracy over decoration. Every number displayed is a claim about money; provenance and freshness matter.
- Multi-tenant: a user may switch client or facility context. `[draft]`
- The platform shows Protected Health Information in production. Patterns MUST NOT include real patient data in examples; use synthetic account identifiers.

---

## 3. Glossary

Define once, use consistently. Agents MUST use these terms and MUST NOT introduce synonyms.

| Term | Meaning |
|---|---|
| Payer | Insurance company or government program that pays claims |
| Claim | Bill submitted to a payer for services |
| Denial | Payer refusal to pay all or part of a claim; has a reason code |
| Appeal | Formal request to reverse a denial |
| Underpayment | Payer paid less than contract rate |
| A/R, A/R days | Accounts receivable; average days from billing to payment |
| Aging bucket | A/R grouped by days outstanding (0-30, 31-60, 61-90, 90+) |
| Clean claim rate | Share of claims accepted first pass without rejection |
| Timely filing | Payer deadline for claim submission; missing it is a denial type |
| Authorization | Payer pre-approval for a service |
| Self-pay | Patient-responsible balance |
| Credit balance | Account overpaid; compliance risk |
| Insight | Ana-generated finding: anomaly, risk, or improvement, with metric, why it matters, suggested action |
| Worklist | Prioritized queue of accounts for a user to act on |
| Drill-in | Navigating from an aggregate (KPI, chart segment, table row) to the underlying detail while keeping filter context |
| Drill-through | Navigating from one app or dashboard to another app with context passed along |
| Connected apps | Two surfaces that pass context between them (e.g. Analytics KPI to FLO worklist) |
| Shell | The persistent frame: sidebar, optional Ana panel, content area, optional toolbar |
| Sidebar | Left vertical container for destinations (where you go). Collapsed (icon-only) and expanded (icon + label) states, `layout/sidebar-collapsed` and `layout/sidebar-expanded` |
| Toolbar | Right vertical container for actions on the current view (what you do here): favorites, quick access, export, reload, feedback |
| Panel | Surface that opens inside the shell without navigating away (Ana panel, action panel, item history). Contains content, not just controls |
| Menu | A list of options that opens on demand from a trigger and closes after choice (user menu, context menu, dropdown) |

---

## 4. Design principles

1. AI first, not AI only. Ana is the entry point for questions and the source of proactive insights, but every insight links to the deterministic view (dashboard, worklist, account) that lets a user verify it. No dead-end AI output.
2. One shell. Every surface renders inside the same sidebar and content area. Apps do not bring their own global navigation.
3. Context survives navigation. Filters, selected client, date range, and drill path persist across drill-in, drill-through, and back.
4. Dense but scannable. Default to compact density; use typography scale and surface tokens, not extra whitespace, to create hierarchy.
5. Explicit states. Every data region defines loading, empty, error, no-permission, and stale states. Agents MUST generate all five.
6. Dark is default, light is supported, device follows OS. Tokens only; no literal values of any kind. `[verified from prototype theme selector]`
7. Numbers are sacred. Right-aligned, mono, consistent precision, explicit units, never truncated without a tooltip.

---

## 5. UI kit boundary: components the patterns may reference

Component sets in the Kinetic library, grouped. Patterns reference these by name. If a pattern needs a component not listed, it is a kit request, not a pattern.

Navigation: Navigation bars/Side bar, Left menu, Right menu, Top bar, CV navigation bar (KIT REQUEST: rename Left menu to Sidebar and Right menu to Toolbar to match the glossary); Menu items/Left menu items, Bar item, Profile, Profile menu, Side bar/Item card, Context menu; Breadcrumbs; Tabs (Top bar, KPI Segments, Segments control Default/Ghost/Outline/Rounded); Navigation/Stepper.

Inputs: Buttons/General (primary, cta, secondary, ghost, danger), Outline, Text button, Icon button; Inputs/Text input, Text area, Search field, Date field, Phone, Currency, Grouped, Authorization fields, Chat; Dropdowns/Dropdown, Dropdown list, Multiselect, Calendar, Time picker; Checkboxes/General, Checkbox with selection, Permissions, Reco Engine List Item; Radio; Switcher/General (toggle), Switcher/Button (segmented); Selections/Arrow switches; AdvancedUserFilters; Tables/Table filters; thumbsup, thumbsdown.

Data display: Tables/Card grid, Headers, Card grid data row, Flo grid data field; Cards/Users, Group Membership, Assigned Permissions, Inherited Permission, Rec Engine Action, Process Preview; Badges/Status, Tag, Chips, Dot, Filter; Avatars; Icon/Priority; Timeline item; Event item; Accordions.

Feedback: Notification; Panels/Alerts; Tooltips/Infoblock, Validation, Black; Tooltip; Loaders/Spinner, Progress indicator, Progress indicator XS, Skeleton loader, Grid loaders, Segments loaders; banner-notifications; warning-banner.

Overlays: Modals, Modals/Status Modal, Modals/File Upload, Info modal; Headers/Modal, Panels, Item history, User Manager, Conversations panel, Chat; Panels/Action, Item History, Flo, Flo Rules, Worklist Option, Conversation, Chat.

AI (Ana): Conversation item/Chat/Ana response, User response, Chat reminder, Conversation panel elements, Conversations list items; Icon/Ana/Rounded chat icons, Animation; Ana/Buttons (in review); Inputs/Chat.

Known kit gaps (found by search, absent from library): pagination, slider, popover, drawer, empty state, chart components, KPI tile (only Tabs/KPI Segments), footer, standalone link, form layout. Patterns that need these will name the gap in `kit-components` as `MISSING: <name>`. The same applies to variables: token names in section 6 under `layout/`, `border/`, and `motion/` do not exist in the kit yet and are open `TOKEN REQUEST`s for the kit lane to define.

---

## 6. UX elements and behaviors to document

This is the pattern backlog. Each row becomes one file in `patterns/` using `PATTERN_TEMPLATE.md`. IDs are stable; names may change. Phase per the three-phase plan plus Phase 0.

### Phase 0: foundations for the library itself
| ID | Pattern | Notes |
|---|---|---|
| lib-template-01 | Pattern template and frontmatter schema | `PATTERN_TEMPLATE.md` |
| lib-index-01 | Index and loading rules for agents | `INDEX.md` |
| lib-glossary-01 | Glossary | Section 3 above; move to own file when it grows |
| lib-inventory-01 | Inventory of current apps and known inconsistencies | To be done with screenshots of live VQ8 apps |

### Phase 1: shell, navigation, identity, global states
| ID | Pattern | Kit components | Key decisions to capture |
|---|---|---|---|
| nav-shell-01 | App shell layout | Side bar, Panels | Outer gutter `layout/shell-gutter` on all sides; sidebar + optional Ana panel + content; no global top bar `[verified from prototype]`; where app-level toolbars go |
| nav-sidebar-01 | Sidebar | Side bar, Side bar/Item card, Search field, Segments control, Switcher | Written: `patterns/nav-sidebar-01.md` |
| nav-toolbar-01 | Right toolbar: contents and states | Right menu, Icon button | Which actions qualify (view-level only); order; pinned-bottom item (feedback); collapsed-only vs labeled; hide when the view has no actions |
| nav-user-01 | User menu placement and contents | Menu items/Profile, Profile menu | Contents: theme selector, Profile, User Management (role-gated), Manage Quick Access Buttons (admin), Logout |
| nav-ana-01 | Ana panel: open, collapsed, closed | Panels/Conversation, Inputs/Chat | Opens as left column at `layout/panel-ana-expanded` (not below `layout/panel-ana-min`), collapses to `layout/panel-ana-collapsed`, closes; sidebar Ana block hides when panel is open; New conversation and History entry points |
| nav-home-01 | Home / Command Center content tabs | Tabs | Live Insight Feed, AI Suggested Dashboards, Saved, Last Opened; analysis view replaces tabs when Ana produces an analysis |
| nav-tabs-01 | In-page tabs and segmented controls | Tabs, Segments control | When tabs vs segments vs filter chips; max count; URL binding |
| nav-breadcrumb-01 | Breadcrumb and location indicator | Breadcrumbs | Path shows client / area / item; truncation; clickable ancestors |
| nav-client-01 | Client and facility context switcher | Dropdown | Where it lives, how switching resets or keeps filters `[draft: not in prototype]` |
| nav-alerts-01 | Alerts entry point and list | Notification, alerts icon | Badge count, list panel vs page, mark read |
| nav-help-01 | Help entry point | Help item | Contents, external vs in-app |
| state-loading-01 | Loading states | Skeleton, Grid loaders, Segments loaders, Spinner | Skeleton for known layout, spinner for unknown; never both; minimum display time |
| state-empty-01 | Empty states | MISSING: empty state | First-use vs filtered-to-nothing vs no access; icon, title, one line, one action; copy pattern from prototype "Nothing opened today / Items you view will appear here" |
| state-error-01 | Error states | Panels/Alerts, warning-banner | Inline region error vs page error; retry; error id for support |
| state-permission-01 | No-permission states | Modals/Status Modal | Hide vs disable vs explain; rule per element type |
| state-stale-01 | Data freshness and stale indicators | Badges/Status, Tooltip | Last refreshed timestamp; stale threshold; reload affordance |
| fb-toast-01 | Toasts and inline confirmations | Notification, banner-notifications | Duration, stacking, position, undo |
| fb-validation-01 | Form validation | Tooltips/Validation, Text input | Inline on blur, summary on submit, error copy format |
| fb-confirm-01 | Destructive action confirmation | Modals/Status Modal, Buttons danger | When a modal is required; wording; default focus on cancel |
| theme-01 | Theme switching | User menu | Light, dark, device; token behavior; persistence |

### Phase 2: drill-ins, connected apps, tables, contextual actions
| ID | Pattern | Kit components | Key decisions to capture |
|---|---|---|---|
| drill-in-01 | Drill-in from aggregate to detail | Card grid, KPI Segments, Breadcrumbs | What is clickable (KPI, chart segment, row); context carried; how to go back; open in place vs panel vs new view |
| drill-through-01 | Drill-through between connected apps | Side bar, Panels | Analytics to FLO worklist, Insight to dashboard, Policy Pulse to affected accounts; context contract (client, filters, date range, entity ids); return path |
| drill-panel-01 | Detail side panel vs full page | Panels/Action, Item History | Threshold for panel; width; stacking rule (one panel at a time) |
| ctx-rightclick-01 | Right-click context menu | Menu items/Context menu | Which surfaces support it (table rows, cards, chart marks); item order (primary action, open in, copy, save, admin); keyboard equivalent; never the only path |
| ctx-rowactions-01 | Row hover actions and kebab menu | Card grid data row, Icon button | Hover reveal vs always visible; max visible actions |
| table-01 | Data table baseline | Card grid, Headers, Table filters | Zebra rows, sticky header, pinned columns, density, numeric alignment, column resize |
| table-sort-filter-01 | Sorting and filtering | sort, filter, AdvancedUserFilters, Filter badge | Filter bar location; applied filter chips; clear all; saved filters |
| table-select-bulk-01 | Selection and bulk actions | Checkbox with selection, bulk-select | Selection bar appearance; select all across pages; bulk action placement |
| table-paging-01 | Pagination and virtual scroll | MISSING: pagination | When to page vs scroll; page size; row count display |
| search-01 | Global and in-page search | Search field, Inputs/Chat | Global search vs Ask Ana; scoping; results grouping |
| filter-global-01 | Global filters (client, date range, payer) | Dropdown, Date field, Calendar | Placement, persistence, interaction with drill-in |
| worklist-01 | Worklist and prioritized queue | Flo grid, Panels/Worklist Option, Icon/Priority | Priority display, claim vs done, next item behavior |
| insight-card-01 | Ana insight card | Cards, Badges/Status | Type (anomaly, risk, improvement), metric + change, why it matters, suggested action, timestamp, actions (investigate with Ana, open view, save) |
| reco-01 | Recommendation and action cards | Cards/Rec Engine Action, Process Preview, Reco Engine List Item | Accept, dismiss, snooze; explanation; audit trail |
| ana-conv-01 | Ana conversation surface | Conversation items, Inputs/Chat | Message types, citations to views, highlight linked insight in feed, pre-filled prompts ("Ask Ana." links) |
| ana-handoff-01 | Ana to deterministic view handoff | Highlight context | When Ana references an item, feed scrolls and highlights it (`border/emphasis` in `brand/primary`, `motion/duration-slow`) `[verified from prototype]` |
| save-fav-01 | Favorites, Quick Access, Last Opened | Star, Item card | User favorites vs admin-pinned Quick Access; Last Opened grouping today / yesterday / earlier; type badges dashboard, report, insight |
| export-01 | Export and share | Right menu (pdf, excel, copy) | Placement in right menu; formats; PHI warning |
| history-01 | Item history and audit | Panels/Item History, Timeline item | Event list format, who did what when |
| perm-01 | Users, groups, permissions UI | Cards/Users, Permissions, User Manager | Inherited vs assigned display |

### Phase 3: subtle details
| ID | Pattern | Notes |
|---|---|---|
| num-format-01 | Number, currency, percent, date formatting | Precision, units, negative values, abbreviated large numbers, `font-family/mono`, right alignment |
| motion-01 | Motion and transitions | Panel open/close `motion/duration-base`, hover `motion/duration-fast`, `easing/standard`, reduced motion |
| kbd-01 | Keyboard navigation and shortcuts | Focus order, sidebar navigation, table navigation, escape closes panel |
| a11y-01 | Accessibility baseline | Contrast on dark, focus visible, aria labels for icon-only controls, screen reader for KPIs |
| copy-01 | Microcopy and tone | Sentence case, verbs on buttons, no exclamation marks, how Ana speaks vs system messages |
| density-01 | Density modes | Compact default; comfortable option; what changes |
| tooltip-01 | Tooltips and infoblocks | Delay, content limits, when required (icon-only, truncated) |
| badge-01 | Status, tag, chip semantics | Which badge for which meaning; color mapping to semantic tokens |
| chart-interaction-01 | Chart hover, select, drill | Tooltip content, selection highlighting, legend behavior (chart visuals owned by Kinetic dataviz) |
| print-01 | Print and PDF layout | What collapses, what is hidden |

---

## 7. Rules for agents generating VisiQuate UI

Shell and navigation
- MUST render inside the shell (nav-shell-01). MUST NOT add a second global navigation or a top bar.
- MUST place the user menu in exactly the location nav-user-01 specifies, nowhere else.
- MUST keep the sidebar group order: core views, TOOLS, footer (nav-sidebar-01).
- MUST put destinations in the sidebar and view actions in the toolbar.
- MUST use glossary names for shell parts.

Components and tokens
- MUST use Kinetic components and variables. MUST NOT write any literal value: no px, rem, ms, %, hex, or numeric weights anywhere in patterns or generated UI. Every dimension, color, radius, shadow, type size, weight, border, and duration is a token reference.
- MUST use `font-family/mono` for all numerals in KPIs, tables, and timestamps.
- MUST use `accent/interactive` for selection and checked states; `brand/primary` is for CTA and Ana identity only.
- MUST NOT create a new component. If one is missing, output `KIT REQUEST: <component>` and use the closest existing one.
- MUST NOT invent a value when a token is missing. Output `TOKEN REQUEST: <proposed name>` and reference that name.

States and data
- MUST define loading, empty, error, no-permission, and stale for every data region.
- MUST show data freshness for any financial figure.
- MUST NOT use real patient or account identifiers in examples.

AI surfaces
- MUST link every Ana insight or recommendation to a deterministic view.
- MUST label AI-generated content as Ana's and keep system messages visually distinct.

Output
- MUST list applied pattern IDs.
- MUST list deviations with a one-line reason.
- MUST list open questions instead of guessing when a pattern is `proposed` or missing.
