# AGENTS.md - VQ8 UX Patterns Library

Version 0.1 (Phase 0 draft). Owner: Anton Malashkevych, Senior Design Manager. Status of every fact below: `[verified]` = confirmed from a source, `[draft]` = needs owner confirmation.

This file is the entry point for any AI agent or human generating, reviewing, or implementing VisiQuate product UI. Read it first. Then load only the pattern files you need from `patterns/` via `INDEX.md`.

---

## 1. How to use this library

1. Read this file fully. It carries business context, the product map, the UI kit boundary, and the rules.
2. Open `INDEX.md`. Load only the patterns whose `applies-to` matches the screen you are working on. Do not load everything.
3. Compose the screen from Kinetic UI kit components (section 5) arranged according to the loaded patterns (section 6). Never redefine a kit component inside a pattern.
4. In your output, cite pattern IDs you applied (`nav-shell`, `state-empty`). If two patterns conflict, or the brief requires something no pattern covers, stop and report the gap. Do not invent a resolution silently.
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
| Command Center, Live Insight Feed, Favorites, Last Opened | Home views: insight feed, favorites, recently opened items | Sidebar, core group; starrable, starred items can be pinned to top |
| Alerts | Alert list; the only badged item | Sidebar, TOOLS group |
| Ask Ana, Help, User | Ask Ana focuses the Ana input (shortcut `/`); Help; user opens the user menu | Sidebar footer |

### 2.4 Users
Primary: revenue cycle directors and managers, denials and appeals specialists, billing and coding staff, patient access staff, payer relations, compliance. Secondary: CFO and executive leadership consuming summaries and forecasts. Users work in dense data all day, often across several payers and facilities, and are measured on dollars recovered, A/R days, and denial rate. `[verified from marketing, roles need confirmation against actual personas]`

### 2.5 Constraints that shape UX
- Data density is a feature. Tables, KPIs, and financial numbers dominate. Numerals use `font-family/mono` for alignment and digit clarity. `[verified from Kinetic typography page]`
- Accuracy over decoration. Every number displayed is a claim about money; provenance and freshness matter.
- Single tenant per login: a user signs in to one tenant environment; there is no in-app client switching.
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
3. Context survives navigation. Filters, date range, and drill path persist across drill-in, drill-through, and back.
4. Dense but scannable. Default to compact density; use typography scale and surface tokens, not extra whitespace, to create hierarchy.
5. Explicit states. Every data region defines loading, empty, error, no-permission, and stale states. Agents MUST generate all five.
6. Dark is default, light is supported, device follows OS. Tokens only; no literal values of any kind. `[verified from prototype theme selector]`
7. Numbers are sacred. Right-aligned, mono, consistent precision, explicit units, never truncated without a tooltip.

---

## 5. UI kit boundary: components the patterns may reference

Component sets in the Kinetic library, grouped. Patterns reference these by name. If a pattern needs a component not listed, it is a kit request, not a pattern.

Navigation: Navigation bars/Side bar, Navigation bars/Left menu (KIT REQUEST: deprecate, replaced by Side bar), Navigation bars/Right menu (KIT REQUEST: rename to Toolbar), Navigation bars/Top bar, Navigation bars/CV navigation bar; Menu items/Left menu items, Menu items/Bar item, Menu items/Name (unused since Top bar no longer shows the user), Menu items/Profile, Menu items/Profile menu, Menu items/Side bar/Item card, Menu items/Context menu; Breadcrumbs; Tabs (Top bar, KPI Segments, Segments control Default/Ghost/Outline/Rounded); Navigation/Stepper.

Inputs: Buttons/General (primary, cta, secondary, ghost, danger), Outline, Text button, Icon button; Inputs/Text input, Text area, Search field, Date field, Phone, Currency, Grouped, Authorization fields, Chat; Dropdowns/Dropdown, Dropdown list, Multiselect, Calendar, Time picker; Checkboxes/General, Checkbox with selection, Permissions, Reco Engine List Item; Radio; Switcher/General (toggle), Switcher/Button (segmented); Selections/Arrow switches; AdvancedUserFilters; Tables/Table filters; thumbsup, thumbsdown.

Data display: Tables/Card grid, Headers, Card grid data row, Flo grid data field; Cards/Users, Group Membership, Assigned Permissions, Inherited Permission, Rec Engine Action, Process Preview; Badges/Status, Tag, Chips, Dot, Filter; Primitives/Avatars; Icon/Priority; Timeline item; Event item; Accordions.

Feedback: Notification; Panels/Alerts; Tooltips/Infoblock, Validation, Black; Tooltip; Loaders/Spinner, Progress indicator, Progress indicator XS, Skeleton loader, Grid loaders, Segments loaders; banner-notifications; warning-banner.

Overlays: Modals, Modals/Status Modal, Modals/File Upload, Info modal; Headers/Modal, Panels, Item history, User Manager, Conversations panel, Chat; Panels/Action, Item History, Flo, Flo Rules, Worklist Option, Conversation, Chat.

AI (Ana): Conversation item/Chat/Ana response, User response, Chat reminder, Conversation panel elements, Conversations list items; Icon/Ana/Rounded chat icons, Animation; Ana/Buttons (in review); Inputs/Chat.

Known kit gaps (found by search, absent from library): pagination, slider, popover, drawer, empty state, chart components, KPI tile (only Tabs/KPI Segments), footer, standalone link, form layout. Patterns that need these will name the gap in `kit-components` as `MISSING: <name>`. The same applies to variables: a pattern names a missing token as `TOKEN REQUEST: <name>` in its `kit-notes`; `layout/` and `motion/` tokens are the current requests.

---

## 6. UX elements and behaviors to document

This is the pattern backlog. Each row becomes one file in `patterns/` using `PATTERN_TEMPLATE.md`. IDs are stable; names may change. Phase per the three-phase plan plus Phase 0.

### Phase 0: foundations for the library itself
| ID | Pattern | Notes |
|---|---|---|
| lib-template | Pattern template and frontmatter schema | `PATTERN_TEMPLATE.md` |
| lib-index | Index and loading rules for agents | `INDEX.md` |
| lib-glossary | Glossary | Section 3 above; move to own file when it grows |
| lib-inventory | Inventory of current apps and known inconsistencies | To be done with screenshots of live VQ8 apps |

### Phase 1: shell, navigation, identity, global states
| ID | Pattern | Kit components | Key decisions to capture |
|---|---|---|---|
| nav-shell | App shell layout | Side bar, Panels | Outer gutter `layout/shell-gutter` on all sides; sidebar + optional Ana panel + content; no global top bar `[verified from prototype]`; where app-level toolbars go |
| nav-sidebar | Sidebar | Navigation bars/Side bar, Menu items/Side bar/Item card, Inputs/Search field, Tabs/Segments control/Default, Switcher/General, Primitives/Avatars | Written: `patterns/nav-sidebar.md` |
| nav-toolbar | Toolbar | Navigation bars/Right menu, Menu items/Bar item, Menu items/Profile | Written: `patterns/nav-toolbar.md` |
| nav-user-menu | User menu placement and contents | Menu items/Profile, Profile menu | Contents: theme selector, Profile, User Management (role-gated), Manage Quick Access Buttons (admin), Logout |
| nav-ana-panel | Ana panel | Panels/Chat, Headers/Chat, Inputs/Chat, Conversation item/Chat, Conversation item/Molecules/Conversations list items, Icon/Ana/Rounded chat icons | Written: `patterns/nav-ana-panel.md` |
| nav-content-tabs | Content tabs | Navigation bars/Top bar, Tabs/Top bar, Selections/Arrow switches, Badges/Status | Written: `patterns/nav-content-tabs.md` |
| nav-cvbar | CV navigation bar | Navigation bars/CV navigation bar, Tabs/Atoms/Segments control/Rounded, Tabs/Atoms/Segment | Written: `patterns/nav-cvbar.md` |
| nav-breadcrumb | Breadcrumbs | Breadcrumbs, Tooltips/Black | Written: `patterns/nav-breadcrumb.md` |
| nav-stepper | Stepper | Navigation/Stepper, Navigation/Atom/Stepper, Foundations/Divider/Horizontal | Written: `patterns/nav-stepper.md` |
| nav-reports-tree | Reports tree | Panels/Reports, Headers/Panels, Menu items/Left menu items, Breadcrumbs, Inputs/Search field | Written: `patterns/nav-reports-tree.md` |
| panel-base | Panel | Panels/*, Headers/Panels, Buttons/Icon button/Additional | Written: `patterns/panel-base.md` |
| nav-alerts | Alerts panel | Panels/Alerts, Headers/Panels, Tabs/Segments control/Default, Tables/Flo grid data field | Written: `patterns/nav-alerts.md` |
| nav-help | Help entry point | Help item | Contents, external vs in-app |
| state-loading | Loading states | Skeleton, Grid loaders, Segments loaders, Spinner | Skeleton for known layout, spinner for unknown; never both; minimum display time |
| state-empty | Empty states | MISSING: empty state | First-use vs filtered-to-nothing vs no access; icon, title, one line, one action; copy pattern from prototype "Nothing opened today / Items you view will appear here" |
| state-error | Error states | Panels/Alerts, warning-banner | Inline region error vs page error; retry; error id for support |
| state-permission | No-permission states | Modals/Status Modal | Hide vs disable vs explain; rule per element type |
| state-stale | Data freshness and stale indicators | Badges/Status, Tooltip | Last refreshed timestamp; stale threshold; reload affordance |
| fb-toast | Toasts and inline confirmations | Notification, banner-notifications | Duration, stacking, position, undo |
| fb-validation | Form validation | Tooltips/Validation, Text input | Inline on blur, summary on submit, error copy format |
| fb-confirm | Confirmation dialog | Modals, Buttons/General, Buttons/Icon button/Additional | Written: `patterns/fb-confirm.md` |
| fb-status-dialog | Status dialog | Modals/Status Modal, Buttons/General | Written: `patterns/fb-status-dialog.md` |
| theme-switch | Theme switching | User menu | Light, dark, device; token behavior; persistence |

### Phase 2: drill-ins, connected apps, tables, contextual actions
| ID | Pattern | Kit components | Key decisions to capture |
|---|---|---|---|
| drill-in | Drill-in from aggregate to detail | Card grid, KPI Segments, Breadcrumbs | What is clickable (KPI, chart segment, row); context carried; how to go back; open in place vs panel vs new view |
| drill-through | Drill-through between connected apps | Side bar, Panels | Analytics to FLO worklist, Insight to dashboard, Policy Pulse to affected accounts; context contract (filters, date range, entity ids); return path |
| ctx-rightclick | Right-click context menu | Menu items/Context menu | Which surfaces support it (table rows, cards, chart marks); item order (primary action, open in, copy, save, admin); keyboard equivalent; never the only path |
| ctx-rowactions | Row hover actions and kebab menu | Card grid data row, Icon button | Hover reveal vs always visible; max visible actions |
| table-base | Data table baseline | Card grid, Headers, Table filters | Zebra rows, sticky header, pinned columns, density, numeric alignment, column resize |
| table-sort-filter | Sorting and filtering | sort, filter, AdvancedUserFilters, Filter badge | Filter bar location; applied filter chips; clear all; saved filters |
| table-select-bulk | Selection and bulk actions | Checkbox with selection, bulk-select | Selection bar appearance; select all across pages; bulk action placement |
| table-paging | Pagination and virtual scroll | MISSING: pagination | When to page vs scroll; page size; row count display |
| search | Global and in-page search | Search field, Inputs/Chat | Global search vs Ask Ana; scoping; results grouping |
| filter-global | Global filters (date range, payer, facility) | Dropdown, Date field, Calendar | Placement, persistence, interaction with drill-in |
| worklist | Worklist and prioritized queue | Flo grid, Panels/Worklist Option, Icon/Priority | Priority display, claim vs done, next item behavior |
| insight-card | Ana insight card | Cards, Badges/Status | Type (anomaly, risk, improvement), metric + change, why it matters, suggested action, timestamp, actions (investigate with Ana, open view, save) |
| recommendation-card | Recommendation and action cards | Cards/Rec Engine Action, Process Preview, Reco Engine List Item | Accept, dismiss, snooze; explanation; audit trail |
| ana-conv | Ana conversation surface | Conversation items, Inputs/Chat | Message types, citations to views, highlight linked insight in feed, pre-filled prompts ("Ask Ana." links) |
| ana-handoff | Ana to deterministic view handoff | Highlight context | When Ana references an item, feed scrolls and highlights it (`border/emphasis` in `brand/primary`, `motion/duration-slow`) `[verified from prototype]` |
| save-favorites | Favorites, Quick Access, Last Opened | Star, Item card | User favorites vs admin-pinned Quick Access; Last Opened grouping today / yesterday / earlier; type badges dashboard, report, insight |
| export-share | Export and share | Right menu (pdf, excel, copy) | Placement in right menu; formats; PHI warning |
| item-history | Item history and audit | Panels/Item History, Timeline item | Event list format, who did what when |
| permissions-ui | Users, groups, permissions UI | Cards/Users, Permissions, User Manager | Inherited vs assigned display |

### Phase 3: subtle details
| ID | Pattern | Notes |
|---|---|---|
| num-format | Number, currency, percent, date formatting | Precision, units, negative values, abbreviated large numbers, `font-family/mono`, right alignment |
| motion | Motion and transitions | Panel open/close `motion/duration-base`, hover `motion/duration-fast`, `easing/standard`, reduced motion |
| keyboard-nav | Keyboard navigation and shortcuts | Focus order, sidebar navigation, table navigation, escape closes panel |
| accessibility | Accessibility baseline | Contrast on dark, focus visible, aria labels for icon-only controls, screen reader for KPIs |
| microcopy | Microcopy and tone | Sentence case, verbs on buttons, no exclamation marks, how Ana speaks vs system messages |
| density-modes | Density modes | Compact default; comfortable option; what changes |
| tooltip | Tooltips and infoblocks | Delay, content limits, when required (icon-only, truncated) |
| badge-semantics | Status, tag, chip semantics | Which badge for which meaning; color mapping to semantic tokens |
| chart-interaction | Chart hover, select, drill | Tooltip content, selection highlighting, legend behavior (chart visuals owned by Kinetic dataviz) |
| print-layout | Print and PDF layout | What collapses, what is hidden |

---

## 7. Rules for agents generating VisiQuate UI

Shell and navigation
- MUST render inside the shell (nav-shell). MUST NOT add a second global navigation or a top bar.
- MUST place the user menu in exactly the location nav-user-menu specifies, nowhere else.
- MUST keep the sidebar group order: core views, TOOLS, footer (nav-sidebar).
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
