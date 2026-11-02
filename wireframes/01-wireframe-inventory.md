# Wireframe Inventory & Consistency Guide

This document provides a complete inventory of the wireframes, maps them to design decision IDs, and documents the consistency requirements an implementation must satisfy.

---

## Wireframe Inventory

---

### navigation/

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `sidebar-expanded.png` | SHELL-1 through SHELL-6 | Sidebar with labels, ACCOUNT section, theme switch, collapse button |
| `sidebar-collapsed.png` | SHELL-1 through SHELL-6 | Icons-only 56px sidebar, theme/expand at bottom |
| `sidebar-functions-light.png` | FNLIST-11 | LIBRARY section after Blocks->Functions replacement (FunctionSquare icon, active). Light theme. |
| `sidebar-functions-dark.png` | FNLIST-11 | Same, dark theme. |
| `sidebar-no-search-{light,dark}.png` | SHELL-8 | Sidebar without the search field: today's struck-through search box with its Ctrl+K badge, the resulting nav starting straight at Dashboard, and the collapsed rail with no search icon. Both themes. |

---

### dashboard/

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `dashboard-populated.png` | DASH-1 through DASH-3 | Summary cards, Recent Activity, Running Executions, Quick Actions |
| `dashboard-empty.png` | DASH-1 through DASH-3 | Zero counts, empty state messages, "Take a Tour" CTA |

---

### lists-build/

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `tests-list-populated.png` | LIST-1 through LIST-9, BULK-1 through BULK-4 | 9 rows with status, pagination, Mass Action button |
| `tests-list-empty.png` | LIST-6 | Green flask icon, encouraging CTA |
| `tests-list-selection-active.png` | BULK-1 through BULK-4 | Checkboxes visible, 0 selected, dropdown disabled |
| `tests-list-selection-partial.png` | BULK-1 through BULK-4 | 3 of 9 selected, dropdown open |
| `tests-list-selection-all.png` | BULK-1 through BULK-4 | All 50 selected, dropdown open |
| `suites-list-populated.png` | LIST-1 through LIST-9, BULK-1 through BULK-4 | 9 rows with test counts, Mass Action button |
| `suites-list-empty.png` | LIST-6 | Blue folder icon, encouraging CTA |
| `regressions-list-populated.png` | LIST-1 through LIST-9 | 9 rows with suite counts (no Mass Action) |
| `regressions-list-empty.png` | LIST-6 | Purple layers icon |
| `executions-list-populated.png` | LIST-1 through LIST-9 | 9 rows, 7 columns (no "New" button per LIST-8) |
| `executions-list-empty.png` | LIST-6 | Blue circle-play icon, "Go to Tests" CTA |
| `list-loading.png` | LIST-4 | Generic loading state: 9 skeleton rows, skeleton pagination |
| `list-error.png` | LIST-5 | Generic error state: red alert icon, "Try Again" button |
| `list-blocked.png` | LIST-10 through LIST-17 | Generic blocked state after a failed supporting read, shown over the Profiles list: route content blurred and inert with the sidebar still live, centered card with warning icon, "Could not load environments", "This page cannot be used until it loads." and Try Again. Two frames, details folded and details open with the panel scrolling and its copy control. The blue "STILL WORKS" pill on the sidebar is an annotation marking the region that stays live, not a product element. Light theme. |

---

### canvas/

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `canvas-empty.png` | CANVAS-29 through CANVAS-34 | Start node, ghost connector, placeholder with "Take a Tour" |
| `canvas-populated.png` | CANVAS-1 through CANVAS-3 | Base layout: Nav \| Palette \| Canvas + Console \| Variable Manager |
| `canvas-element-selected.png` | CANVAS-35 through CANVAS-44, CANVAS-143 through CANVAS-145 | White dashed halo, action row, kebab menu open |
| `canvas-running.png` | CANVAS-74 through CANVAS-78 | Execution controls, element border states, console with output |
| `canvas-debug-paused.png` | CANVAS-79 through CANVAS-88 | Step controls, amber paused element, breakpoint dot |
| `canvas-breadcrumb-modes-light.png` | BC-1 through BC-6 | All 6 breadcrumb modes in light theme: standalone Test exec, Suite child exec, Regression child exec, Tests-origin edit, Suite-origin edit, Regression-origin edit. Entity icons (Play/GitBranch/FolderKanban/TestTubeDiagonal) match sidebar; ghost-button hover pill on intermediate segments; last segment non-interactive. |
| `canvas-breadcrumb-modes-dark.png` | BC-1 through BC-6 | Same as light, dark theme. |
| `canvas-breadcrumb-truncation-light.png` | BC-7 (states A/B/C) | Truncation states in light theme: A everything fits, B parents collapse to single actionable `...` (popover open shows parent list - reuses EntityListPopover from collision-resolution-modal.tsx), C leaf truncates after collapse with hover popover (reuses TruncatedName tooltip from data-table column-factories.tsx). |
| `canvas-breadcrumb-truncation-dark.png` | BC-7 (states A/B/C) | Same as light, dark theme. |
| `quick-add-popover-light.png` | CANVAS-223 through CANVAS-226 | Ctrl+Space quick-add popover (top-center over the canvas): fuzzy search input, grouped PLUGINS / CONTROLS / FUNCTIONS results (Function rows carry version badge; "New Function" creator row), footer key hints for Enter / Ctrl+Enter / Alt+Enter / Esc / drag. Light theme. Superseded by `quick-insert-window-{light,dark}.png` for the window shape, key set and search rule. |
| `quick-add-popover-dark.png` | CANVAS-223 through CANVAS-226 | Same as light, dark theme. |
| `quick-insert-window-{light,dark}.png` | CANVAS-231 through CANVAS-237 | Quick Insert as a movable window: header drag handle with title + close and no grip mark (matching the other 11 draggable sheets), grouped PLUGINS / CONTROLS / FUNCTIONS list with the first result highlighted, footer hints (arrows + Tab navigate, Enter add where the flow is, Ctrl+Enter add at center, PgUp/PgDn page, Esc close, pointer badge + click a row to add, pointer badge + drag). The seven hints wrap onto two rows, which is what sets the window height. Shown opened with no query, filtered on "as" with the Enter hint naming the selection anchor, and with no match - the empty result keeps its footer. Both themes. Superseded by `quick-insert-functions-{paged,status}-{light,dark}.png` for the Functions group (creator row now leads it, published rows alphabetical) and for the permanent status line under the list. |
| `quick-insert-functions-paged-{light,dark}.png` | CANVAS-241, CANVAS-242, CANVAS-245 | Live captures of the server-paged Functions half at true size, three states side by side: opened with no query and more pages remaining ("42 Functions - refine your search to narrow down"), scrolled to the end with every page pulled in ("42 Functions"), and filtered on "as" where one page covers the match ("8 Functions"). Shows the status line sitting between the list and the hint strip, and the built-in rows filtering alongside the server rows. Both themes. |
| `quick-insert-functions-status-{light,dark}.png` | CANVAS-242 through CANVAS-247 | The status line states no steady capture can show, six panels drawn to the real window geometry: first fetch in flight ("Loading Functions…"), next page in flight ("Loading more Functions…"), a query no Function matches (no FUNCTIONS heading at all, "No Functions match"), an empty library (creator row alone under the heading, "No Functions published yet"), a failed fetch (warning icon + "Couldn't load Functions" + "Try again", in view on an unfiltered open where the group is forty rows below the fold), and the Functions group in order (creator row first, published rows alphabetical). The line keeps one height in every state, so the window height and the hint strip never move. Both themes. |
| `session-mirror-holders-{light,dark}.png` | SESS-1 through SESS-4 | Read-only mirror of a session held by someone else: person (indigo) + assistant (violet, "(MCP)" + See connection) banner below the breadcrumb; canvas + Variable Manager mirrored. Both themes. |
| `session-mirror-detached-{light,dark}.png` | SESS-2, SESS-11, SESS-12 | The same mirror once its holder is gone and nobody was promoted: amber banner reading "Read-only - nobody holds the workbench" with a struck-through eye, Watch Session and See Connection inert with the tooltips that explain why, and the take action reading Take Session rather than Take Over. The canvas the watcher was already shown stays put and the Variable Manager reports the snapshot is empty. Both themes. |
| `session-takeover-{light,dark}.png` | SESS-5 through SESS-8 | Take-over flow: requester waiting modal + Force Take Over; person-holder approval modal; the person / assistant / idle / force rules. Both themes. |
| `session-mirror-person-connection-{light,dark}.png` | WSRV-9 | Person-holder mirror banner gaining a real connection identity ("another session on Chrome (macOS)") and the See Connection affordance in the person's indigo tone, beside Follow Changes and Take Over. Both themes. |
| `canvas/watch-mode-block-pulse-{light,dark}.png` | WATCH-1 through WATCH-3, WATCH-5 through WATCH-7 | Watch-mode on a mirrored canvas: the violet MCP banner carrying the Follow Changes toggle over the read-only workflow; the canvas controls cluster is zoom/fit only (no on-canvas focus control). The assistant's active block carries a steady violet border and a one-shot ring at runtime (WATCH-3), verified by the watch-mode functional tests. Both themes. |
| `canvas/watch-mode-var-pulse-{light,dark}.png` | WATCH-4 | Variable Manager while mirrored: rows are clean by default (no all-rows bar). A just-changed variable's row briefly shows a violet left bar that pulses and fades at runtime (WATCH-4), verified by the watch-mode functional tests. Both themes. |
| `session-mirror-run-{light,dark}.png` | RUNM-1 through RUNM-4 | Watcher's workbench during a mirrored run (assistant holder shown): violet banner with trailing phrase "read-only, running live"; toolbar edit group disabled with the run's environment read-only in the selector slot ("Env:" idiom from the Execution History page) and Focus Current as the only live control; canvas painted with run states and Console panel streaming the run's lines. Both themes. |

---

### workbench/

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `workbench-breadcrumbs-bar.png` | CANVAS-68, CANVAS-69 | Breadcrumb row with Reset link and status indicator |
| `workbench-console-expanded.png` | CANVAS-4 through CANVAS-8 | Console 200px, tabs inline, "Clear Output" with confirmation |
| `vmgr-panel.png` | VMGR-1 through VMGR-14 | Variable Manager panel: header (title + Add), filter + sort toolbar, flat row list with two-line grid, four-icon action cluster (eye, expand, edit, delete), type-colored badges with type rightmost. Covers REQ-3.1.3.11, REQ-3.1.3.12, REQ-3.2.2.18 |
| `vmgr-inspect-modal-shell-{light,dark}.png` | VMGR-15 through VMGR-18 | Variable inspect modal shell (string variable, Current mode): header with grip / mono name / type badge / close, full-value body in type color, footer (text-label Mode trigger, centered metric `3 chars`), corner resize grip; the italic `read-only` hint drawn in the footer is superseded by VMGR-18 (no action zone). Covers REQ-3.1.3.11, REQ-3.2.2.18 |
| `vmgr-inspect-modal-modes-{light,dark}.png` | VMGR-19 | Inspect modal modes: Initial (value dim + italic, `Initial` trigger) beside Current with the Mode menu open (text + check items, Initial / Current, opens upward) |
| `vmgr-inspect-modal-context-{light,dark}.png` | VMGR-20 through VMGR-22 | Panel rows with the open-modal source-row indicator (2px indigo inset edge + tint + indigo expand icon); expression variable modal (`{x}` header badge, cyan source dim + italic, metric `expression`); integer modal with empty metric zone |
| `vmgr-inspect-complex-bodies-{light,dark}.png` | VMGR-23 through VMGR-27, VMGR-30 | Inspect modal complex Visual bodies: array (muted 0-based index column + value rows), map (key + value rows), table (mini-grid, sticky uppercase header, leading muted 0-based `#` row-index column, 480px default). Per-cell tinting by the value's own type; nested maps/arrays as compact tinted JSON. Footer shows the View dropdown right of Mode and the complex metrics `5 items` / `4 keys` / `3 rows x 4 cols`. Covers REQ-3.1.3.11, REQ-3.2.2.18 |
| `vmgr-inspect-code-view-{light,dark}.png` | VMGR-28, VMGR-29 | Inspect modal Code view: read-only CodeMirror JSON surface (existing editor stack tinting, line numbers), 2-space pretty-print, table as array-of-row-objects; View dropdown open state (text trigger, upward menu Visual / Code with check) |
| `vmgr-inspect-complex-states-{light,dark}.png` | VMGR-31 through VMGR-34 | Inspect modal complex states: Initial mode (whole body dim + italic), empty value (`no items` centered muted line, `0 items` metric), first full-value fetch skeleton (skeleton only on first fetch; stale-while-revalidate afterwards) |
| `vmgr-inspect-expression-views-{light,dark}.png` | VMGR-35 through VMGR-39 | Inspect modal expression views: Literal view rendering the evaluated value exactly like a literal (quoted, type color; cyan reserved for source), Expression view rendering the cyan raw source, scalar View menu (Literal / Expression, text + check), complex expression View menu (Visual / Code / Expression). Covers REQ-3.1.3.11, REQ-3.1.3.13, REQ-3.2.2.18 |
| `vmgr-inspect-expression-states-{light,dark}.png` | VMGR-38, VMGR-40, VMGR-41 | Inspect modal expression states: `Not evaluated yet.` centered muted italic empty state with `no value yet` metric; Initial mode showing the dim italic source with the View dropdown disabled on `Expression` |
| `vmgr-inspect-type-mismatch-{light,dark}.png` | VMGR-42 | Inspect modal type-mismatch safeguard: amber italic `received <actual> - declared <declared>` notice, raw value rendered below tinted by its actual type, amber `type mismatch` metric; scalar and complex variants |
| `vmgr-inspect-compare-{light,dark}.png` | VMGR-43 through VMGR-48 | Inspect modal Compare mode: Compare as the third Mode entry with the upward menu (Initial / Current / Compare), side-by-side panes (Initial dim + italic left, Current right) for string, array, table, and expression watchers, in-pane uppercase pane labels (`Initial - source` / `Current - evaluated` for expressions), the delta metric family (`42 -> 84 chars`, `3 -> 4 items`, `1 -> 3 rows`, `expression -> 44 chars`, `expression -> no value yet`), and the View dropdown disabled showing `Literal` on expression scalars. Covers REQ-3.1.3.11, REQ-3.1.3.13, REQ-3.2.2.18 |
| `vmgr-string-formats-{light,dark}.png` | VMGR-65 through VMGR-68 | Inspect modal string Format control: read view with auto-detected JSON syntax-highlighted and the footer Format dropdown `Auto (JSON)` in the view slot (VMGR-65, VMGR-66); edit frame superseded by `workbench/vmgr-one-window-*.png` (VMGR-106, VMGR-110); the Format menu (text + check, opens upward) listing Auto (JSON) / Plain / JSON / XML / YAML (VMGR-65); advisory lint - invalid JSON underlined with Save still enabled (VMGR-67). (Template is a value kind, not a format - see `vmgr-inspect-template`.) Covers REQ-3.1.3.11 |
| `vmgr-inspect-template-{light,dark}.png` | VMGR-72 through VMGR-75 | Template as a first-class string value kind: the panel row + modal header cyan `{{ }}` kind badge with STRING type (VMGR-72); the watcher Rendered / Template View pair mirroring the expression Last Evaluated / Expression (VMGR-73); edit frame superseded by `workbench/vmgr-one-window-*.png` (VMGR-106, VMGR-110); the Format dropdown no longer offering Template (VMGR-75). Covers REQ-3.1.3.11, REQ-3.1.3.13, REQ-3.1.3.15 |
| `vmgr-one-window-variable-{light,dark}.png` | VMGR-106, VMGR-108, VMGR-109, VMGR-110, VMGR-114 | One window for adding and editing a variable: New variable (Map, `{}`), Edit with Initial, Edit with Current; every field enabled in both values, the value switch pill right after the Value label, the icon-only Open editor button, Cancel / Save (Add: Cancel / Create). Covers REQ-3.1.3.11, REQ-3.1.3.24 |
| `vmgr-one-window-value-field-{light,dark}.png` | VMGR-110, VMGR-111 | The window's value field per type: String, Integer, Boolean, Array, Map `{}`, Table cut with "…", Set to null ticked (Kind hidden, one grayed `null` field), secret dots, Expression. Covers REQ-3.1.3.24, REQ-3.1.3.6. Field look on Block windows superseded by `workbench/field-block-states-*.png` (FIELD-1..6). |
| `vmgr-one-window-input-{light,dark}.png` | VMGR-108, VMGR-111, VMGR-112, VMGR-113, VMGR-114 | Enum input `env`: New (Default value `dev`), Edit with Default just turned into an enum (empty select outlined in red, "Default value is required", Save disabled), Edit with Current `staging`; plain Required input `host` with an empty default. Covers REQ-3.1.2.10, REQ-3.1.2.11, REQ-3.1.3.24 |
| `field-block-states-{light,dark}.png` | FIELD-1, FIELD-2, FIELD-3, FIELD-4, FIELD-5, FIELD-6, FIELD-8 | Function Block window `deploy_check` with every input in the one value field, followed by two fixed icon columns, expand (two diagonal arrows) and `{ }`; the choice list `env` leaves the expand column empty. `region` not set shows its default `eu-west-1` in upright gray, with the tooltip "Not set, so the default is used. Type to use your own value."; `owner` holds the user's `qa-team` in the string color, with the reset icon inside the field at the right end; `prefix` holds empty text, shown as italic gray `<empty string>`; `note` shows italic gray `null` with the pressed null icon inside the field; `tags` not set shows `["smoke"]` in gray; `targets` holds one computed entry, drawn on one line as `["web-1", {{ backup_host }}, "web-3"]` with `{{ backup_host }}` in the expression color and no quotes, with the tooltip "Has {{ }} entries. Open the editor to change it."; the required choice list `env` holds `staging`. Covers REQ-3.1.1.5, REQ-3.1.2.10, REQ-3.1.2.11, REQ-3.1.3.20, REQ-3.1.3.21, REQ-3.1.3.24 |
| `field-switch-warning-{light,dark}.png` | FIELD-7 | `{ }` clicked on `owner` while it holds `qa-team`: the Function Block window dimmed behind the confirmation dialog "Switch the field to an expression?" with "The current value is cleared." and the buttons Cancel, Clear & Default and Clear & Empty (primary). Covers REQ-3.1.1.5 |
| `field-time-picker-{light,dark}.png` | FIELD-9 | OpenSearch Block window: From and To are the one value field with the clock icon inside on the left; From holds `now-15m` in the string color, To is not set and shows its default `now` in gray. The time picker is open from From's expand icon (Absolute / Relative / Now, 15 minutes ago, Round to the minute, result `now-15m`) and ends with a Cancel / Save footer. Covers REQ-3.3.2.3, REQ-3.1.1.5 |
| `field-list-fields-{light,dark}.png` | FIELD-10 | List settings as one-line fields with expand and `{ }`: OpenSearch Fields `["@timestamp", "message"]` and Stats cut with "…"; Python Arguments `["alpha", {{ run_id }}]` with the computed entry in the expression color; HTTP Parts cut with "…" in the Body group; in the TLS / Certificates group, Verify Server Certificate with its label in full and Cipher Suites not set, showing the default cipher list in gray cut with "…". Covers REQ-3.1.1.5, REQ-3.1.3.19 |
| `field-variable-required-{light,dark}.png` | FIELD-12 | New variable window as opened: a red star after Name and "Name is required" under the empty Name field, outlined in red, from the start; Create disabled. Covers REQ-3.1.3.11, REQ-3.1.3.24 |
| `field-icons-{light,dark}.png` | FIELD-11 | Icons: the Variable Manager row `run_id` with Inspect as a magnifying glass, and the Edit value sheet header with the full-size button as a four-corner frame, above a value field whose expand icon stays the two diagonal arrows. Covers REQ-3.1.3.11 |
| `vmgr-complex-value-grid-{light,dark}.png` | VMGR-81, VMGR-82 | Complex Visual editor (array / map / table) redesign: the grid wrapped in an outlined, rounded container with an isolated quiet header row - array `#  /  Value  /  Type`, map `Key  /  Value  /  Type`, the table's existing column header banded the same way; value-first row order with a smaller trailing type pill; hairline row dividers (VMGR-82). Table column widths become sticky - a manual resize survives add / remove / move column and the Visual <-> Code round-trip by living in the persistent editor state rather than the re-mounting table body (VMGR-81). Covers REQ-3.1.3.11 |
| `vmgr-setter-rows-{light,dark}.png` | VMGR-83 | Variable Setter rows: the compact row layout and `{ }` literal-expression toggle are unchanged; integer / float / boolean edit inline (shared scalar bodies, exact-text numbers), an expression edits inline in the cyan field with no `{x}` badge (the toggle conveys the kind), and string / array / map / table show an `Edit` preview button opening the shared value editor. Covers REQ-3.4.1.14, REQ-3.1.3.11, REQ-3.1.3.13 |
| `vmgr-setter-value-editor-string-{light,dark}.png` | VMGR-84 | Variable Setter string value editor: the shared string body in a sheet with a static `Edit value` header + STRING badge (no name / rename - those live on the row); footer Kind dropdown (Literal / Template, opens upward) beside the Format dropdown (Auto / Plain / JSON / XML / YAML), Literal keeps Format active with advisory lint, Template hides Format and shows `{{ }}` highlighting + autocomplete; no Mode pill. Covers REQ-3.4.1.14, REQ-3.1.3.11, REQ-3.1.3.15 |
| `vmgr-setter-value-editor-complex-{light,dark}.png` | VMGR-85 | Variable Setter complex value editor: the shared array / map / table body (per-element / per-column type pills, Visual / Code, exact-number guard, shared validators) in a sheet with the static `Edit value` header + type badge and no name / rename; footer View dropdown (Visual / Code) + metric + Cancel / Save, Format pretty-print button in Code, no Mode pill. Deletes the legacy table editor modal (last consumer). Covers REQ-3.4.1.14, REQ-3.1.3.11 |
| `vmgr-entity-vars-{light,dark}.png` | VMGR-86, VMGR-87 | Entity-scope variable tables (Edit Suite / Regression / System Variables) on the shared bodies: the authoring chrome (select / name / type / secret / delete + `+ Add`) is unchanged; the Value column replaces the one-line JSON text input with the shared per-type affordance - integer / float / boolean inline, string + array / map / table an `Edit` preview button (string preview in the string color, complex a muted `N items` / `N keys` summary) opening the shared literal-only `Edit value` sheet, and a secret value the uniform pencil + lock + masked-dots clear-and-edit. The array row no longer fails "Must be valid JSON format" (divergence D-4 fixed). The sheets themselves reuse `vmgr-setter-value-editor-{string,complex}-*`; the per-type cell affordances mirror `profiles/vmgr-profile-param-cell-*`. Covers REQ-3.1.3.1, REQ-3.1.3.11 |
| `profiles/vmgr-profile-param-cell-{light,dark}.png` + `vmgr-setter-value-editor-string-{light,dark}.png` (reused) | - | Element-config string parameters on the shared value editor: every string parameter (single- AND multi-line, previously only multiline) replaces its inline text box with the shared `ValueField` preview + Edit affordance opening the shared `Edit value` sheet (Literal / Template Kind + Format + `{{ }}`), exactly as the profile param rows and Variable Setter (`vmgr-setter-rows-*`). Expression stays the inline `{}` toggle; literal / template / expression are mutually exclusive per parameter. Plus a backend hardening (LD-99): strict single-line + enum string params trim their resolved value so an accidental newline (from the multiline-capable sheet, or an expression result) cannot break a URL / path / enum; free-form + multiline payloads preserved. No new visual surface - reuses the approved profile/setter wireframes. Covers REQ-3.1.1.5, REQ-3.4.2.2, REQ-3.1.3.15 |
| `workbench/vmgr-c7-modal-structure-{light,dark}.png` | VMGR-92 | JSON/XML config restructure: four peer sections top-to-bottom - Input Parameters (content only) -> Queries (lifted out of Output Variables) -> Output Mode (Combined/Individual radio mirroring Assert Branching Mode) -> Output Variables (success/errors/results bindings). `output_mode` is no longer an input-param row; the pointless `{}` toggle is gone. Covers REQ-3.4.2.2 |
| `workbench/vmgr-c7-json-body-locked-{light,dark}.png` | VMGR-88 | Locked data format: the json/xml content `Edit value` sheet shows the Format dropdown disabled + pinned to `JSON`/`XML` (no Auto). Covers REQ-3.4.2.2, REQ-3.6.2.2 |
| `workbench/vmgr-c7-json-body-invalid-{light,dark}.png` | VMGR-89 | Blocking literal validation: an ill-formed JSON body raises the shared validation strip with `(+N more)` and disables Save (blocking, unlike the advisory free-form lint). Covers REQ-3.6.2.2, REQ-3.6.2.4 |
| `workbench/vmgr-c7-strict-string-plain-{light,dark}.png` | VMGR-90 | Strict string lock: the URL (and CA cert / file path) `Edit value` sheet shows the Format dropdown disabled + pinned to `Plain` (no Auto, no Format button). Covers REQ-3.4.2.2 |
| `workbench/vmgr-c7-save-reason-{light,dark}.png` | VMGR-91 | Eager save-blocking reasons: an un-named query row is outlined red with `Name is required` shown immediately, so the disabled Save always has a visible culprit. Covers REQ-3.4.2.2 |
| `vmgr-null-rows-dark.png` | VMGR-93 | Variable Manager rows: a null value of each of the seven types beside its empty value; Function parameters with null input, output and local |
| `vmgr-null-watcher-dark.png` | VMGR-93, VMGR-94 | Watchers for a null string, integer, table and array and an empty array, `null` / `no items` centered |
| `vmgr-null-entity-vars-dark.png` | VMGR-93 | Suite and system variable tables with null values |
| `vmgr-secret-save-warning-dark.png` | SECUI-12 | The confirmation over the block config sheet, in the warning look of the shared confirmation dialog with a red confirm: (a) one variable - "Make this variable secret?" naming `token`; (b) several - "Make 3 variables secret?" over a bordered mono list of the names; buttons "Cancel" / "Make secret and save". The dialog body text follows SECUI-12's current wording; the PNG still shows the earlier sentence. Covers REQ-4.5.20 |
| `workbench-fn-call-enum-secret-dark.png` | FNCFG-6, FNCFG-7, SECUI-10, SECUI-11 | Function block config sheet: the `api_key` secret input drawn as a block's secret field (pencil, dots, lock, expression button); the `retries` integer enum input as the block-config select with its list open (1, 2, 10), required star and expression button; the `region` plain expression field; the outputs table row `token` / String / Secret ticked / `auth_token`. Covers REQ-3.1.2.9, REQ-3.1.2.11 |
| `workbench-run-dialog.png` | RUN-1 through RUN-15 | Persistent header selector, split button pattern |
| `workbench-debug-dialogs.png` | DEBUG-1 through DEBUG-8 | Debug dropdown, debug options popover |
| `workbench-environments-dialog.png` | ENV-1 through ENV-16 | Searchable popup, RECENT + ALL sections |

---

### tools-palette/

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `palette-controls-section.png` | CANVAS-97 through CANVAS-104 | All controls with color-coded icons |
| `palette-plugins-section.png` | CANVAS-105 through CANVAS-111 | All plugins organized by category |
| `remote-icons.png` | REMICON-1 | Remote-section icon redesign (Set A): before vs proposed, both themes, legend, and palette order for the 6 SSH plugins + Remote Execution. SFTP, which keeps its own glyph and sits between SSH Tunnel Close and Remote Execution (REMICON-1, SFTP-10), is not drawn |
| `palette-collapsed.png` | CANVAS-13 through CANVAS-18 | 44px width, icons only with flyout menus |
| `palette-recents.png` | CANVAS-9 through CANVAS-12 | Recents section flyout with 8 recent items |
| `palette-most-used.png` | CANVAS-9 through CANVAS-12 | Most Used section flyout with 8 frequent items |
| `palette-fn-bottom-expanded-light.png` | CANVAS-200 through CANVAS-203 | Real-UI capture of the expanded palette with bottom buttons renamed: "+ New Function" (drag handle) + "Function Lib" (opens library modal). No in-palette Functions section. Light theme. |
| `palette-fn-bottom-expanded-dark.png` | CANVAS-200 through CANVAS-203 | Same as above, dark theme. |
| `palette-fn-bottom-collapsed-light.png` | CANVAS-200 through CANVAS-203 | Collapsed 64px icon strip with bottom icons unchanged (Plus, Blocks) but tooltips rename to "New Function" / "Function Lib". Light theme. |
| `palette-fn-bottom-collapsed-dark.png` | CANVAS-200 through CANVAS-203 | Same as above, dark theme. |
| `palette-empty-group-removed-{light,dark}.png` | PLUGIN-11 | PLUGINS section before and after: today's CUSTOM group at count 0 with its "No custom plugins" empty state struck through, and the resulting list ending at DATA. Both themes. |

---

### historical/

Superseded wireframes are kept under this directory for reference. They do NOT govern current implementation.

#### historical/blocks/ (pre-Function era)

These wireframes predate the Block→Function rename.

| File | Description |
|------|-------------|
| `blocks-library-modal.png` | Pre-Function library modal (title "Blocks Library", single tag dropdown). Superseded by `function-lifecycle/library-modal-populated-*.png`. |
| `block-publish-dialog.png` | Pre-Function publish modal with Update/New toggle. A new library entry and a new version of an existing entry now open separate dialogs (FN-VER-3). Superseded by `function-lifecycle/publish-dialog-*.png`. |

#### historical/canvas/ (superseded by `canvas-node/` + `function-canvas/`)

Pre-redesign canvas / palette / element-config snapshots.

| File | Description |
|------|-------------|
| `blocks-library-modal.png` | Earlier draft of the Blocks Library modal (before the `blocks/` finalization). |
| `element-configuration-modal.png` | Pre-redesign element-config modal. Superseded by `modals-elements/element-configuration-modal.png`. |
| `palette-controls-section.png`, `palette-plugins-section.png`, `palette-full-design.png` | Pre-redesign palette layouts. Superseded by `tools-palette/`. |
| `test-canvas-empty.png`, `test-canvas-populated.png`, `test-canvas-running.png`, `test-canvas-debug-paused.png`, `test-canvas-element-selected.png`, `test-canvas-palette-collapsed.png`, `test-canvas-console-expanded.png`, `test-canvas-variable-manager-expanded.png` | Pre-redesign workbench-canvas states. Superseded by the `canvas/` directory (current) and `canvas-node/` (redesign). |
| `workbench-block-publish.png` | Pre-Function publish dialog draft. Superseded by `function-lifecycle/publish-dialog-*.png`. |
| `workbench-debug-dialogs.png`, `workbench-environments-dialog.png`, `workbench-run-dialog.png` | Pre-redesign workbench dialog snapshots. Superseded by `workbench/workbench-*-dialog.png` (current). |

#### historical/executions/

| File | Description |
|------|-------------|
| `regression-execution.png`, `suite-execution.png` | Pre-redesign execution detail views. Superseded by the current Reports / Executions design. |

#### historical/forms/ (superseded by inline-create patterns)

| File | Description |
|------|-------------|
| `regression-create-edit.png`, `suite-create-edit.png`, `suite-delete.png` | Pre-redesign create/edit/delete dialogs. Superseded by the current inline-create + EntityPickerModal patterns on the list pages. |

#### historical/library/

| File | Description |
|------|-------------|
| `blocks-list-populated.png` | Pre-Function `/blocks` list page. Superseded by `lists-library/blocks-list-populated.png` (current) and by the `/functions` page. |
| `plugins-list-populated.png` | Pre-redesign plugins list page. |

#### historical/lists/

| File | Description |
|------|-------------|
| `executions-list-{empty,error,loading,populated}.png` | Pre-redesign Executions list states. Superseded by the current Executions list page. |
| `regressions-list-{empty,error,loading,populated,run}.png` | Pre-redesign Regressions list states. Superseded by the current Regressions list page. |
| `suites-list-{empty,error,loading,populated}.png` | Pre-redesign Suites list states. Superseded by the current Suites list page. |

#### historical/workbench/

| File | Description |
|------|-------------|
| `workbench-vars-manager-expanded.png` | Pre-redesign Variable Manager. Superseded by `workbench/vmgr-panel.png` (current) and `function-canvas/01-var-mgr-grouped-*.png` (drilled-in Function variant). |
| `vmgr-inspect-edit-scalar-{light,dark}.png` | Inspect modal edit state (scalar): Current/idle read-only with the footer `Edit` button (VMGR-61 - editing acts on the current value, which equals the definition while idle); editing state with the indigo modal halo and the locked Mode pill (VMGR-62), the header name turned into a rename-with-refactoring input, the value body turned into an editable field, and Cancel / Save replacing the read-only hint. Covers REQ-3.1.3.11, REQ-3.2.2.18. Was VMGR-61, VMGR-62. Superseded by `workbench/vmgr-one-window-*.png` (VMGR-106..114). |
| `vmgr-inspect-edit-complex-{light,dark}.png` | Inspect modal edit state (array, map): the read-only Visual body becomes inline per-element inputs keeping their type color on the contained, header-banded grid (VMGR-82), with per-row delete (and reorder for arrays) and an `+ Add item` / `+ Add entry` line; footer shows the Mode pill locked while the View dropdown stays enabled so Visual/Code stay switchable mid-edit (VMGR-62). Covers REQ-3.1.3.11, REQ-3.2.2.18. Was VMGR-62, VMGR-82. Superseded by `workbench/vmgr-one-window-*.png` (VMGR-106..114). |
| `vmgr-inspect-edit-code-{light,dark}.png` | Inspect modal Code editing: the read-only CodeMirror JSON surface becomes writable with the indigo edit chrome (VMGR-62) and a footer `Format` button between View and the metric, shown only while editing in Code; the invalid-JSON guard - the linter underlines the parse error, the View menu's `Visual` item is disabled with the immediate tooltip `Fix JSON errors to switch to Visual`, and `Format` + `Save` are disabled until it parses. Covers REQ-3.1.3.11. Was VMGR-62. Superseded by `workbench/vmgr-one-window-*.png` (VMGR-106..114). |
| `vmgr-inspect-edit-expression-{light,dark}.png` | Inspect modal expression editing: the cyan source field editing the expression's source, never its evaluated value (VMGR-63, reusing the existing ExpressionField micro-IDE) with variable autocomplete and expand-to-full-editor, the View dropdown pinned to `Expression` and locked while editing; the design-time validation failure state - a circular-reference (cycle) error with the field's destructive border, the inline message, and `Save` disabled (design-time gate only). Covers REQ-3.1.3.11, REQ-3.1.3.13. Was VMGR-63. Superseded by `workbench/vmgr-one-window-*.png` (VMGR-106..114). |
| `vmgr-inspect-edit-table-{light,dark}.png` | Inspect modal table editing: read-only 0-based `#` index column, each column header is a name input spanning the cell width plus a full-name type select (`string` / `integer` / `float` / `boolean`) on the banded header row (VMGR-82); editable cells tinted by column type; a per-column `⋮` menu on the type row with Move left / Move right / Delete column (Delete disabled at one column); a trailing `+` header to add a column, `+ Add row`, and per-row delete on hover, with horizontal scroll in the narrow sheet. The add / delete / move column ops carry their sticky widths (VMGR-81). Covers REQ-3.1.3.11. Was VMGR-81, VMGR-82. Superseded by `workbench/vmgr-one-window-*.png` (VMGR-106..114). |
| `vmgr-inspect-current-edit-{light,dark}.png` | Inspect modal Current-edit (runtime override): the Current-mode read-only footer turns into an `Edit` gate when the test is paused/stopped (VMGR-61); the Mode control rendered as a prominent color-coded pill - amber `Current` (live/transient), indigo `Initial` (definition) - shown editing the definition vs the live value, with the indigo edit chrome kept identical so the pill alone signals what changes (VMGR-62). Covers REQ-3.2.1.6. Was VMGR-61, VMGR-62. Superseded by `workbench/vmgr-one-window-*.png` (VMGR-106..114). |
| `vmgr-inspect-edit-table-validation-{light,dark}.png` | Inspect modal table validation: one shared schema validator wired into both views. Empty or duplicate column names mark the header inputs with the destructive border the cells already use (VMGR-69); an out-of-type cell stays red and the validation strip names the first problem by priority with a `(+N more)` count, Save disabled (VMGR-70); the Code view type-checks cell values against the Visual-owned schema and flags unknown / missing columns, gating Save the same way (VMGR-71). Covers REQ-3.1.3.11. Was VMGR-69, VMGR-70, VMGR-71. Superseded by `workbench/vmgr-one-window-*.png` (VMGR-106..114). |
| `vmgr-create-modal-{light,dark}.png` | Create-in-modal: `+ Add` opens the floating modal in a create state instead of the legacy scalar dialog, complex types created inline with no Visual-Editor hop; labeled-form layout - Name on its own row, then Type + Kind as two inline dropdowns (Kind = Literal / Expression / Template for strings, Literal / Expression otherwise; Kind drives the value body), Mark-as-secret; Function input/output parameter declaration absorbed mode-aware via the in-Function `+ Add ▾` - IN/OUT header badge, resizable multiline Description, Required (input), Create-enum + Value Type + "Allowed values" (input + array), default-value labeling, and literal-only param defaults (no Kind; outputs gain Kind per VMGR-99, `vmgr-create-output-param-dark.png`); destructive type-change confirm reused from `ConfirmationDialog`; create can Mark-as-secret while secret rows stay blocked from the modal afterward. Covers REQ-3.1.3.11, REQ-3.1.2.1, REQ-3.1.3.13, REQ-3.1.3.15. Superseded by `workbench/vmgr-one-window-*.png` (VMGR-106..114). |
| `vmgr-create-input-param-dark.png` | New input parameter, Array: enum off (typed grid, Visual / Code) and enum on (Required locked, Set to null disabled, Value Type, Allowed values without a Type column). Covers REQ-3.1.3.24, REQ-3.1.3.11, REQ-3.1.2.1. Was VMGR-97, VMGR-98, VMGR-100. Superseded by `workbench/vmgr-one-window-*.png` (VMGR-106..114). |
| `vmgr-create-input-default-rules-dark.png` | New input parameter window in the VMGR-98 layout, three states: (a) Type String, Required ticked - no Create enum row, Set to null ticked and disabled, one disabled `null` default field, tooltip "A required input has no default: the caller always gives the value. To run this Function alone, set the input's Current value."; (b) Type Array, Mark as secret ticked - Create enum disabled with the italic hint "off while secret is set", Set to null ticked and disabled, tooltip "A secret input has no default: the caller gives the value."; (c) Array enum, Value Type Integer, allowed 1 / 2 / 10 with no Type column, Required locked "locked on while enum is set", Mark as secret disabled "off while enum is set", Set to null unticked and disabled. Covers REQ-3.1.2.10, REQ-3.1.2.11. Was VMGR-103, VMGR-104. Superseded by `workbench/vmgr-one-window-*.png` (VMGR-106..114). |
| `vmgr-create-set-to-null-dark.png` | New variable window, Set to null unticked (String, Literal) and ticked (Array, Kind hidden, `null` field). Covers REQ-3.1.3.24, REQ-3.1.3.11. Was VMGR-97. Superseded by `workbench/vmgr-one-window-*.png` (VMGR-106..114). |
| `vmgr-create-output-param-dark.png` | New output parameter, Integer: Kind Expression with `len(rows)`, and Set to null ticked (Kind hidden). Covers REQ-3.1.3.24, REQ-3.1.3.11, REQ-3.1.2.1, REQ-3.1.2.8. Was VMGR-97, VMGR-98, VMGR-99. Superseded by `workbench/vmgr-one-window-*.png` (VMGR-106..114). |

#### historical/function-canvas/

| File | Description |
|------|-------------|
| `03-param-create-modal-{light,dark}.png` | Create Parameter / Create Variable modal. Three modes shown side by side: Input mode, Output mode, Variable mode (existing, unchanged). One shared component; per-mode customizations are title + subtitle, Default Value helper text, presence of the Required flag (Input only), downstream row landing, and row badge. Was FN-PARAM-1 through FN-PARAM-4. Superseded by `workbench/vmgr-one-window-*.png` (VMGR-106, VMGR-110). |

---

---

### modals-elements/

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `element-configuration-modal.png` | CANVAS-124 through CANVAS-151 | Version dropdown, INPUT/OUTPUT tables, enum toggle |
| `function-config-modal-local-light.png` | CANVAS-207, CANVAS-208, CANVAS-210, CANVAS-211, CANVAS-212, CANVAS-214 | Function instance config modal, Local variant, light theme. L badge before editable name, no version selector, INPUT PARAMETERS + OUTPUT VARIABLES sections (expression bindings + variable pickers), Cancel + Save footer. |
| `function-config-modal-local-dark.png` | CANVAS-207, CANVAS-208, CANVAS-210, CANVAS-211, CANVAS-212, CANVAS-214 | Same as above, dark theme. |
| `function-config-modal-published-light.png` | CANVAS-207, CANVAS-209, CANVAS-210, CANVAS-211, CANVAS-212, CANVAS-214 | Function instance config modal, Published variant, light theme. S badge before read-only name, version dropdown top-right, per-instance editable description, Changelog + Details + Cancel + Save footer. |
| `function-config-modal-published-dark.png` | CANVAS-207, CANVAS-209, CANVAS-210, CANVAS-211, CANVAS-212, CANVAS-214 | Same as above, dark theme. |
| `function-config-modal-empty-light.png` | CANVAS-213 | Empty-section pattern: a Function with zero declared inputs. Section header is kept, italic muted "This Function declares no inputs." line renders between top and bottom dividers. Light theme. |
| `function-config-modal-empty-dark.png` | CANVAS-213 | Same as above, dark theme. |
| `ssh-session-open-config-light.png` | SSH-1 through SSH-5 | SSH Session Open config form on the shared element config sheet: Connection section (expanded, Host/Port/Username/Password/Private Key/Parent Session) with a group description, Advanced section (collapsed, description only), Output Variables (Session ID, Connected, Server Banner, Hop Count) each with `(i)`. Light theme. |
| `ssh-session-open-config-dark.png` | SSH-1 through SSH-5 | Same as above, dark theme. |
| `ssh-tunnel-open-config-light.png` | SSHTUN-1 through SSHTUN-8 | SSH Tunnel Open config form on the shared element config sheet: Forwarding section (expanded, Session ID, Local Port, Remote Host, Remote Port) with a group description, Advanced section (collapsed by default; drawn expanded to show its one Validate Target checkbox, off), Output Variables (Tunnel ID, Local Port) each with `(i)`. Light theme. |
| `ssh-tunnel-open-config-dark.png` | SSHTUN-1 through SSHTUN-8 | Same as above, dark theme. |
| `http-headers-editor-light.png` | HTTP-1 through HTTP-7 | HTTP headers map editor: panel A everyday state (per-row Literal/Expression kind toggles, expression Authorization row via bearer(), "+ Add entry" / "+ Auth" / "+ Content-Type" scaffolds with the media-type menu open, auto-sent-headers note); panel B guard rails under Form body mode (mode-conflict Content-Type row, case-insensitive duplicate pair, amber in-field unsecured-credential advisories on a literal X-Api-Key and an expression with an embedded literal, strip with first message + "(+1 more)", Save disabled). Light theme. Annotation: the kind toggles, "+ Auth" scaffold, bearer() row, and mode-conflict guard rail depict a model the revised HTTP-1..HTTP-7 decisions replace (template strings, Auth section, generated read-only rows, duplicate-based Content-Type rule); the revised decision text governs. |
| `http-headers-editor-dark.png` | HTTP-1 through HTTP-7 | Same as above, dark theme (same annotation). |
| `http-body-modes-light.png` | HTTP-6, HTTP-8, HTTP-9, HTTP-14 | HTTP config sheet body area: panel A GET carrying a Text body (body on every method) with the JSON-without-Content-Type amber in-field advisory; panel B POST in Form (URL-encoded) mode with the Form Fields map row and the muted "set automatically" Content-Type note; panel C the four-mode Body Mode menu. Light theme. Annotation: the bare muted Content-Type note depicts a model the revised HTTP-6/HTTP-9 decisions replace (read-only generated rows, automatic-body-headers control, styled note containers); the revised decision text governs. |
| `http-body-modes-dark.png` | HTTP-6, HTTP-8, HTTP-9, HTTP-14 | Same as above, dark theme (same annotation). |
| `http-multipart-file-light.png` | HTTP-10, HTTP-11 | HTTP body modes continued: panel A Multipart (form-data) on the config sheet (Parts row + generated-boundary note); panel B the Parts editor sheet (Kind/Name/Value-or-Source rows, text part with expression value, file part with artifact:// source, "+ Add part"); panel C File mode with the empty-state file-source forms (artifact://, testdata://, host path) and the auto-from-extension Content-Type note. Light theme. Annotation: the per-row kind toggle and expression part value depict a model the revised HTTP-2/HTTP-10 decisions replace (template strings with the {x} input affordance); the revised decision text governs. |
| `http-multipart-file-dark.png` | HTTP-10, HTTP-11 | Same as above, dark theme (same annotation). |
| `cipher-picker-two-table-light.png` | HTTP-16, HTTP-13 | Cipher picker sheet at the default range (TLS 1.2-1.3): two tables - TLS 1.0-1.2 with per-suite compatibility tags (1.2 / 1.0-1.2) and TLS 1.3 (selectable, untagged) - each with drag handles, blue checkboxes, and both OpenSSL and IANA names. Light theme. |
| `cipher-picker-two-table-dark.png` | HTTP-16, HTTP-13 | Same, dark theme. |
| `cipher-picker-range-hidden-light.png` | HTTP-16 | Cipher picker at a narrowed range (TLS 1.0-1.1): the 1.2-only suites and the entire TLS 1.3 table are hidden, leaving only the suites usable at 1.0-1.1 (out-of-range suites are hidden, not dimmed). Light theme. |
| `cipher-picker-range-hidden-dark.png` | HTTP-16 | Same, dark theme. |
| `http-proxy-row-{light,dark}.png` | HTTP-13 | HTTP block config sheet, Connection group: the Proxy menu open with WAVE setting and Off |
| `http-proxy-row-remote-{light,dark}.png` | HTTP-13 | The same sheet for a block on a remote host: the Proxy row grayed out, naming the remote host's settings |
| `function-config-modal-fixed-light.png` | FNCFG-1, FNCFG-2, FNCFG-4 | Config-modal fixes: aligned INPUT/OUTPUT tables (both info columns), `(i)` on inputs AND outputs with descriptions (tooltip shown), params populated. Light theme. |
| `function-config-modal-fixed-dark.png` | FNCFG-1, FNCFG-2, FNCFG-4 | Same, dark theme. |
| `function-param-create-light.png` | FNCFG-3 | Param-create dialog with the new optional Description field that feeds the `(i)`. Light theme. |
| `csv-config-{light,dark}.png` | CSV-1 through CSV-11 | CSV Parser config on the shared element config sheet: Input Parameters table (Operation, CSV Content, Delimiter, Has header row boolean, Column types = Auto, Empty cells, On type mismatch - each with `(i)`); Transform group with collapsible Sorts (priority list of Name/Index column + direction) and Filters (per-column blocks: Name/Index column + as-Type, Literal operator/value and `_cell` Expression conditions, Add Literal / Add Expression / Add Filter); Output Variables (Table, Row Count, Schema=Array) with the Secret column. Light + dark. |
| `excel-config-read-{light,dark}.png` | XLS-1 through XLS-10, XLS-14 | Excel config in Read mode on the shared element config sheet: flat Input Parameters table (Operation = Read, Workbook required with an `artifact://` / `testdata://` / absolute path, Sheet, Range in A1 notation, Has header row boolean, Header row integer defaulting to 1, Column types = Auto, Empty cells, On type mismatch - each with `(i)`); Secrets group; Transform group with the CSV Sorts and Filters sections reused; Output Variables (Table, Row Count, Schema, Sheets, Success, Errors) with the Secret column. Light + dark. |
| `wait-until-config-{light,dark}.png` | WAIT-1, WAIT-2, WAIT-3, WAIT-4, WAIT-6 | Wait Until config on the shared element config sheet: Input Parameters table (Timeout required, Check Interval defaulting to 1000, optional Timeout Message - each with `(i)`) above the shared assertion builder with its "+ Add Assertion" / "+ Add Group" row; Output Variables (Passed = Boolean, Elapsed = Integer); a WAIT MODE radio section (Retry selected / Watch) where Assert's Branching Mode sits, with the Fail Current Scope checkbox below its divider. Both themes. |
| `parallel-config-{light,dark}.png` | PARALLEL-3, PARALLEL-4, PARALLEL-5, PARALLEL-6 | Parallel config on the shared element config sheet: Name + Version row, Description, an Input Parameters table holding the optional Section Time Limit, a BRANCHES list of rows (BRANCH badge, name field, optional per-branch time limit, reorder arrows, delete) under a Name / Time limit (ms) column header with "+ Branch" below, and a JOIN MODE radio section (Wait for all selected / First to finish) where Wait Until puts WAIT MODE. No Output Variables section - the control binds nothing. Footer carries Changelog / Details / Profiles and Cancel / Save. Both themes. |
| `switch-config-{light,dark}.png` | SWITCH-2, SWITCH-3, SWITCH-4, SWITCH-8, SWITCH-9, SWITCH-10 | Switch/Case config on the shared element config sheet: stacked case cards (chevron, CASE badge, branch name field, Break switch in the header, reorder arrows, delete) with the assertion builder in the expanded body; a collapsed case with Break off showing no extra annotation; the DEFAULT card with the neutral badge, no Break switch and its body caption (superseded 2026-07-31 - the card now reads "Runs when no case matched, or when a case above falls through", see SWITCH-4); "+ Case" and disabled "+ Default" buttons below. Both themes. |
| `excel-config-write-{light,dark}.png` | XLS-1, XLS-3, XLS-11 through XLS-14 | Excel config in Write mode: Operation = Write, Workbook (required), Sheet, Table (required table variable ref carrying the `{}` expression toggle), Write header row boolean, Start cell defaulting to `A1`, "If the file exists" = Keep other sheets; Secrets group; Transform group with the same Sorts and Filters sections Read offers, shaping the rows on their way into the sheet; Output Variables (File, Success, Errors). Light + dark. |
| `config-sheet-cascade-light.png` | CANVAS-227 through CANVAS-230 | Config modals as DraggableSheets: two cascaded sheets (+28px offset) over an interactive canvas with no backdrop; header drag handle with "<Name> - Edit Config" title + X close, right-edge resize affordance. Light theme. |
| `config-sheet-cascade-dark.png` | CANVAS-227 through CANVAS-230 | Same as light, dark theme. |
| `profiles-selection-modal.png` | PROFILE-11 through PROFILE-26 | Bound Profiles + Add Profile sections |
| `profiles-create-edit-modal.png` | PROFILE-27 through PROFILE-53 | Parameter editor with per-environment values |
| `profiles/vmgr-profile-param-cell-{light,dark}.png` | - (REQ-4.7.4) | Profile parameter value cell on the shared bodies: integer/float/boolean edit inline; string + array/map/table open the shared "Edit value" sheet via an Edit button (string preview in the string color, complex a muted summary); a secret param of any type shows the uniform `pencil + lock + masked dots` clear-and-edit affordance; delete is the trash icon. The complex / string sheets themselves reuse `vmgr-setter-value-editor-{complex,string}-*` (string sheet renders Format-only - no Template kind, profiles being literal-only). |
| `profiles-copy-values-modal.png` | PROFILE-43 through PROFILE-50 | RECOMMENDED + OTHER sections |
| `k8s-connect-config-{light,dark}.png` | K8SCON-1 through K8SCON-6 | K8s Connect config on the shared element config sheet, default state: Connection (API URL required, Namespace, Timeout), Authentication (Bearer Token secret + Get SA Token toggle unticked), TLS / Certificates (Verify Server Certificate, CA Certificate, TLS Server Name, Client Certificate + Client Key, Min/Max TLS Version, Cipher Suites), collapsed Secrets, Output Variables (K8s Session with the Secret checkbox checked, Cluster Version). Light + dark. |
| `k8s-connect-config-sa-token-{light,dark}.png` | K8SCON-2 | The same sheet with Get SA Token ticked: Service Account (required), SA Namespace and Duration (s) revealed inside Authentication. Light + dark. |
| `k8s-get-config-{light,dark}.png` | K8SREAD-1, K8SREAD-2, K8SREAD-3, K8SREAD-6, K8SREAD-8, K8SREAD-9, K8SREAD-10 | K8s Get config on the shared element config sheet in the default Name mode: Connection (K8s Session required + secret, Timeout 30), Resource (Resource Type = Default, Kind = Pod with the picker chevron, Search by = Name, Name required, Output Format = Map), Advanced with no All namespaces row and no API version pair (a plain always-visible Namespace, Impersonate user, Impersonate groups), Failure Handling (On error = Fail the block), collapsed Secrets, Output Variables (Result = Map, Names = Array, Count = Integer, Success), with Error and Reason absent in the default On error mode. Light + dark. |
| `k8s-get-config-selector-{light,dark}.png` | K8SREAD-1, K8SREAD-6, K8SREAD-8 | The same sheet with Search by = Selector: the Name row is replaced by Label Selector (app=checkout) and Field Selector (status.phase=Running), Output Format's first option now reads Array, Advanced leads with All namespaces above the plain Namespace field, which hides while All namespaces is ticked, and Result comes back as an Array. Light + dark. |
| `k8s-get-config-list-{light,dark}.png` | K8SREAD-1, K8SREAD-3, K8SREAD-9 | The same sheet with Search by = List: neither the Name row nor the selector rows render, so Resource carries only Resource Type, Kind, Search by and Output Format, whose first option reads Array; Advanced keeps All namespaces above the plain Namespace field, and the outputs are Result = Array, Names = Array, Count = Integer and Success, with Error and Reason absent in the default On error mode. Light + dark. |
| `k8s-get-config-custom-kind-{light,dark}.png` | K8SREAD-2 | The same sheet with Resource Type = Custom: the grouped Kind dropdown is replaced by a plain required string field (VirtualService) with no picker chevron; the rest of the sheet is unchanged. Light + dark. |
| `k8s-get-kind-picker-{light,dark}.png` | K8SREAD-2, K8SREAD-4, K8SREAD-5 | The Kind picker open over the Get sheet: a search field at the top, then the tinted heading bands Workloads, Networking, Config, Storage and Cluster with alphabetical members and inline muted short names (deploy, po, svc, cm, pvc, ns, no). The stored value, Pod, is marked by a check at the end of its row; the highlighted row is the keyboard cursor, which opens on the stored value and then follows typing and the arrow keys, so highlight and check are two different things and can sit on different rows. Light + dark. |
| `k8s-events-config-{light,dark}.png` | K8SREAD-6, K8SREAD-8 through K8SREAD-11 | K8s Events config on the shared element config sheet: Connection (K8s Session, Timeout), Events (Scope to object ticked, then Object Type = Default, Object Kind on the same grouped searchable picker Get carries, Object Name, Kind and Name both required, Event Type = Any, Event Reason, Max Age (s), Max Events, Output Format = Array), Advanced (All namespaces above the plain Namespace field, which hides while All namespaces is ticked, then Impersonate user, Impersonate groups), Failure Handling, collapsed Secrets, Output Variables (Result = Array, Count = Integer, Success), with Error and Reason absent in the default On error mode. Light + dark. |
| `k8s-logs-config-{light,dark}.png` | K8SREAD-8 through K8SREAD-10, K8SREAD-20 | K8s Logs config on the shared element config sheet: Connection, Logs (Pod required, Container required, Previous Instance, Tail Lines, Since (s), Timestamps unticked, Output Format = String offering String and Array while Timestamps is off and String and Table while it is on, Max Bytes), Advanced with no All namespaces row at all and an unconditional plain Namespace field (Namespace, Impersonate user, Impersonate groups), Failure Handling, collapsed Secrets, Output Variables (Logs = String, Success), with Error and Reason absent in the default On error mode. Light + dark. |
| `k8s-top-config-{light,dark}.png` | K8SREAD-8 through K8SREAD-10 | K8s Top config on the shared element config sheet in Pods by name (Select by defaults to All): Connection, Measurement (Measure = Pods, Select by = Name, Name required, Include containers), Advanced with no All namespaces row (a plain Namespace field, Impersonate user, Impersonate groups; All namespaces appears only when Measure is Pods and Select by is All or Selector, and never when Measure is Nodes, which also hides the Namespace field), Failure Handling carrying the Top-specific wording about a cluster with no metrics API, collapsed Secrets, Output Variables (Usage = Table, Count = Integer, Success), with Error and Reason absent in the default On error mode. Light + dark. |
| `k8s-apply-config-{light,dark}.png` | K8SWRITE-1, K8SREAD-10, K8SREAD-12, K8SREAD-14 | K8s Apply config on the shared element config sheet in the default Manifest mode: Connection (K8s Session required + secret, Timeout 30), Resource (Define with = Manifest, Manifest required as a multi-document YAML value, If exists = Update, Output Format = Array), Advanced with a plain always-visible Namespace and no API version pair (Namespace, Impersonate user, Impersonate groups), Failure Handling (On error = Fail the block), collapsed Secrets, Output Variables led by Summary = Table (Result = Array, Names = Array, Count = Integer, Success), with Error and Reason absent in the default On error mode. Light + dark. |
| `k8s-apply-config-form-configmap-{light,dark}.png` | K8SWRITE-1, K8SWRITE-2 | The same sheet with Define with = Form and Kind = ConfigMap: Name (checkout-config) and the Data map editor with its entry-count button replace Manifest, Output Format offers Map as its first option and Result comes back as a Map. Light + dark. |
| `k8s-apply-config-form-secret-{light,dark}.png` | K8SWRITE-3 | Form mode with Kind = Secret: Name (checkout-tls), the Data map editor and Secret Type = Opaque, the type carrying the three values Opaque, kubernetes.io/tls and kubernetes.io/dockerconfigjson; values stay readable while the author types them. Light + dark. |
| `k8s-apply-config-form-job-{light,dark}.png` | K8SWRITE-1, K8SWRITE-4 | Form mode with Kind = Job and Job from = Image: Image required (ghcr.io/acme/migrate:1.4) and Command as a single-line string (/app/migrate --to 1.4), with no Environment row on the sheet. Light + dark. |
| `k8s-apply-config-form-job-cronjob-{light,dark}.png` | K8SWRITE-1 | Form mode with Kind = Job and Job from = CronJob: a single required CronJob Name row (nightly-cleanup) replaces Image and Command, everything else unchanged. Light + dark. |
| `k8s-delete-config-{light,dark}.png` | K8SWRITE-5, K8SWRITE-8, K8SREAD-10, K8SREAD-12, K8SREAD-14 | K8s Delete config on the shared element config sheet deleting by name: Connection, Resource (Resource Type = Default, Kind = Deployment on the grouped picker, Delete by = Name, Name required, Ignore not found unticked with its `{}` toggle, Cascade = Background, Grace Period (s) empty, Wait until gone ticked), no Field Selector row, no All namespaces row and no Output Format row, Advanced (Namespace, Impersonate user, Impersonate groups), Failure Handling, collapsed Secrets, Output Variables led by Summary = Table (Names = Array, Count = Integer, Success), with Error and Reason absent in the default On error mode. Light + dark. |
| `k8s-delete-config-selector-{light,dark}.png` | K8SWRITE-5 | The same sheet with Delete by = Selector: Label Selector (app=checkout) replaces Name and Ignore not found is absent, everything else unchanged. Light + dark. |
| `k8s-scale-config-{light,dark}.png` | K8SWRITE-6, K8SWRITE-8, K8SREAD-10, K8SREAD-12, K8SREAD-14 | K8s Scale config on the shared element config sheet in its only state: Connection, Scale carrying exactly Resource Type = Default, Kind = Deployment, Name required and Replicas = 5, with no precondition pair and no wait row anywhere on the sheet, Advanced (Namespace, Impersonate user, Impersonate groups), Failure Handling, collapsed Secrets, Output Variables Summary = Table then Success only. Light + dark. |
| `k8s-rollout-config-{light,dark}.png` | K8SWRITE-7, K8SWRITE-8, K8SREAD-10, K8SREAD-12, K8SREAD-14 | K8s Rollout config on the shared element config sheet in Restart: Connection, Rollout (Operation = Restart, Kind = Deployment, Name required, To revision absent), Advanced (Namespace, Impersonate user, Impersonate groups), Failure Handling, collapsed Secrets, and two Output Variables, Summary = Table and Success, with Status absent outside the Status operation. Light + dark. |
| `k8s-rollout-config-status-{light,dark}.png` | K8SWRITE-7, K8SWRITE-8 | The same sheet with Operation = Status: the same input rows, with Status = String present in the OUTPUT VARIABLES table between Summary and Success. Light + dark. |
| `k8s-rollout-config-undo-{light,dark}.png` | K8SWRITE-7 | The same sheet with Operation = Undo: an optional To revision integer row is revealed under Name, outputs unchanged at Summary and Success. Light + dark. |
| `k8s-exec-config-{light,dark}.png` | K8SEXEC-1, K8SEXEC-8, K8SEXEC-9 | K8s Exec config on the shared element config sheet in its only state, the header chip carrying the Terminal glyph: Connection (K8s Session required + secret, Timeout 60), Command (Pod required, Container required, Command required as one command line reading `sh -c "echo hi there"`), with no stdin row and no working-directory row anywhere on the sheet, Advanced (Namespace, Impersonate user, Impersonate groups), Failure Handling (On error = Fail the block), collapsed Secrets, Output Variables Stdout = String, Stderr = String, Exit Code = Integer and Success, with Error and Reason absent in the default On error mode. Light + dark. |
| `k8s-script-config-{light,dark}.png` | K8SEXEC-2, K8SEXEC-3, K8SEXEC-8, K8SEXEC-9 | K8s Script config on the shared element config sheet in its only state, the header chip carrying the SquareCode glyph: Connection (K8s Session required + secret, Timeout 60), Script (Pod required, Container required, Interpreter = /bin/sh, Script required as a multi-line code value that is fed to the interpreter on standard input), with no working-directory row and no cluster-version warning row, banner or notice anywhere on the sheet, Advanced (Namespace, Impersonate user, Impersonate groups), Failure Handling (On error = Fail the block), collapsed Secrets, Output Variables Stdout = String, Stderr = String, Exit Code = Integer and Success, with Error and Reason absent in the default On error mode. Light + dark. |
| `k8s-copy-config-{light,dark}.png` | K8SEXEC-4, K8SEXEC-5, K8SEXEC-6, K8SEXEC-7, K8SEXEC-8, K8SEXEC-9 | K8s Copy config on the shared element config sheet with Direction = From Pod, the header chip carrying the ArrowRightLeft glyph: Connection (K8s Session required + secret, Timeout 60), Copy (Direction = From Pod offering From Pod and To Pod, Pod required, Container required, Source Path required reading /var/log/app.log as a path inside the pod, Target Path required reading artifact://app.log on the WAVE side, No Preserve unticked with its `{}` toggle), with no Retries row on the sheet, Advanced (Namespace, Impersonate user, Impersonate groups), Failure Handling (On error = Fail the block), collapsed Secrets, Output Variables Summary = Table then Success only, with no list-of-paths row and no Count, and with Error and Reason absent in the default On error mode. Light + dark. |
| `k8s-copy-config-to-pod-{light,dark}.png` | K8SEXEC-5 | The same sheet with Direction = To Pod: both path labels stay where they are and only their values and info badges follow the direction, Source Path reading artifact://fixtures/seed.json on the WAVE side and Target Path reading /data/seed.json inside the pod; every other input row and both outputs are unchanged. Light + dark. |
| `k8s-copy-config-advanced-{light,dark}.png` | K8SEXEC-10 | The same sheet with Direction = From Pod and Advanced carrying Max size (MiB) 256 and Max files 10000 after Namespace, Impersonate user and Impersonate groups, each with its `{}` toggle, the group footer reading "Namespace and identity in place of what the session provides, and size limits for copies from the pod"; every other row and both outputs are unchanged. Light + dark. |
| `profiles/k8s-profile-config-{light,dark}.png` | K8SPROF-1, K8SPROF-3, K8SPROF-6 | The shipped Create Profile modal with Type = kubernetes: the PARAMETERS header carries `+ Add` and nothing else, and eight parameter rows follow - api_url, token (secret), client_cert, client_key (secret), ca_cert, verify_ssl (Boolean, its secret checkbox disabled, the two-segment control on true), tls_server_name and namespace showing its declared starting value default. No kubeconfig import row anywhere on the modal. Light + dark. |
| `profiles/database-profile-config-{light,dark}.png` | SQL-14, K8SPROF-7, K8SPROF-8 | The Create Profile modal with Type = database: ten parameter rows - host, port (empty, no placeholder), database, username, password (secret), verify_ssl (true), ca_cert, client_cert, client_key (secret), driver_options (0 pairs); no timeout, failover, TLS toggle or database type. Light + dark. |
| `helm-install-config-{light,dark}.png` | HELM-1, HELM-2, HELM-3, HELM-5, HELM-6, HELM-8, HELM-9 | Helm Install config on the shared element config sheet, default state: Connection (K8s Session required, Timeout 300), Install (Release Name required, Chart required, Version, Repository URL, Values, Set, Output Format = Table), collapsed Auth & TLS, collapsed Advanced, Failure Handling (Atomic off, On error = Fail the block), collapsed Secrets, Output Variables Result = Table, Status, Success. No wait row, no Revision output. Light + dark. |
| `helm-upgrade-config-{light,dark}.png` | HELM-1 through HELM-6, HELM-8, HELM-9 | Helm Upgrade, default state: as Install plus Install if missing, Reuse Values, Reset Values (all off) in the Upgrade group and Cleanup on Fail beside Atomic in Failure Handling. Light + dark. |
| `helm-rollback-config-{light,dark}.png` | HELM-1, HELM-2, HELM-3, HELM-6, HELM-9 | Helm Rollback, default state: Connection, Rollback (Release Name required, Revision empty = previous, Output Format = Table), collapsed Advanced without Create Namespace, Failure Handling (Cleanup on Fail off, On error), Output Variables Result, Status, Success. Light + dark. |
| `helm-uninstall-config-{light,dark}.png` | HELM-1, HELM-2, HELM-9, HELM-10 | Helm Uninstall, default state: Connection, Uninstall (Release Name required, Keep History off, Ignore Not Found off, Cascade = background), collapsed Advanced, Failure Handling (On error), Output Variables Success only. Light + dark. |
| `helm-test-config-{light,dark}.png` | HELM-1, HELM-7, HELM-9 | Helm Test, default state: Connection, Test (Release Name required, Logs off, Output Format = Table), collapsed Advanced, Failure Handling, Output Variables Result = Table, Success; no Logs output while Logs is off. Light + dark. |
| `helm-status-config-{light,dark}.png` | HELM-1, HELM-6, HELM-9 | Helm Status, default state: Connection (Timeout 30), Status (Release Name required, Revision empty = current, Output Format = Table), collapsed Advanced, Failure Handling, Output Variables Result, Status, Success. Light + dark. |
| `fileio-config-read-{light,dark}.png` | FIO-1, FIO-2, FIO-4, TDATA-8 | File I/O config, Operation = Read: Path with Browse; collapsed Secrets |
| `fileio-config-write-{light,dark}.png` | FIO-1, FIO-2, FIO-3, FIO-4 | Operation = Write: Path with Browse, Content, If the file exists = Replace it |
| `fileio-config-copy-{light,dark}.png` | FIO-1, FIO-2, FIO-3 | Operation = Copy: Source and Destination with Browse, If the file exists = Replace it |
| `fileio-config-delete-{light,dark}.png` | FIO-1, FIO-5 | Operation = Delete: Path with Browse, Ignore missing off |
| `fileio-config-stats-{light,dark}.png` | FIO-1, FIO-6 | Operation = Stats: Path with Browse, Size, Checksum = None, Output format = Individual |
| `fileio-config-list-{light,dark}.png` | FIO-1, FIO-7 | Operation = List: Path with Browse, RegEx Pattern, Include subfolders, Size |
| `fileio-config-create-folder-{light,dark}.png` | FIO-1, FIO-8 | Operation = Create folder: Path with Browse |
| `fileio-config-output-stats-{light,dark}.png` | FIO-9 | OUTPUT tab for Stats (Individual): Exists, Type, Modified, Size, Checksum with binding controls |
| `fileio-config-output-list-{light,dark}.png` | FIO-9 | OUTPUT tab for List: Entries, Count with binding controls |
| `shell-script-config-source-{light,dark}.png` | SHRUN-3, SHRUN-4, SHRUN-5, SHRUN-9 | Shell Script config, Input Parameters section, the title glyph FileTerminal: Script Type Source with a single-line script, Shell /bin/bash, three Arguments rows ($1 --env, $2 env.name as an expression, $3 3) with the up/down pair and delete, Input Variables with two entries, Execution, Stop on Pattern, Failure Handling and Secrets collapsed. Light + dark. Known deviation: `k8s-script-config-{light,dark}.png` still carries SquareCode, the glyph K8s Script had before the role rule. |
| `shell-script-config-file-{light,dark}.png` | SHRUN-3, TDATA-10 | Shell Script config, Script Type File, Script File testdata://scripts/deploy.sh with Browse; only the Script group differs from shell-script-config-source. Light + dark. |
| `shell-script-config-stop-pattern-{light,dark}.png` | SHRUN-10, SHRUN-12, SHRUN-13, SHRUN-14 | Shell Script config scrolled to Execution (Working Directory /tmp with Browse, Timeout 300, Log Output ticked) and Stop on Pattern expanded with Stop on pattern ticked, Pass pattern ^Server started, Fail pattern ERROR\|FATAL. Light + dark. |
| `shell-script-config-output-{light,dark}.png` | SHRUN-6, SHRUN-8 | Shell Script config, Output Variables section: Stdout, Stderr, Exit Code, Success, then the variable export table with the columns Script Variable, Type, Secret and WAVE Variable holding COUNT bound to pod_count (Integer) and STATUS bound to deploy_status (String), and the Add variable export button as the table's footer row. Light + dark. |
| `shell-exec-config-{light,dark}.png` | SHRUN-17, SHRUN-18, SHRUN-19 | Shell Exec config, Input Parameters section, the title glyph Terminal: Command and Shell (/bin/sh), Input Variables, Execution and Stop on Pattern collapsed, Failure Handling and Secrets collapsed. Light + dark. Known deviation: SSH Session Exec has no wireframe of its own here, so its move to the same Terminal glyph is shown only by this row and `k8s-exec-config-{light,dark}.png`. |
| `python-editor-default-{light,dark}.png` | PYRUN-13, PYRUN-20, PYRUN-21 | Edit value sheet in Python mode with a ten-line script, the F1 Help chip at the footer's left and the Close / Save / Run buttons at its right, Save disabled because the script is unchanged and Run enabled. Light + dark. |
| `python-editor-syntax-errors-{light,dark}.png` | PYRUN-13, PYRUN-21 | Edit value sheet in Python mode with two syntax errors underlined in the script, the validation strip above the footer reading Line 4: '(' was never closed (+1 more), Save enabled and Run disabled while the script does not parse. Light + dark. |
| `python-editor-completion-docs-{light,dark}.png` | PYRUN-13, PYRUN-19 | Edit value sheet in Python mode with the completion list open at the cursor, grouped into Variables and Functions with the typed prefix underlined, and the documentation panel beside the highlighted readings entry naming its origin, columns and table access. Light + dark. |
| `python-editor-rename-{light,dark}.png` | PYRUN-19 | Edit value sheet in Python mode with the inline rename box anchored under the selected symbol values, every occurrence highlighted, the current name pre-filled and the hint Rename symbol, Enter to apply, Esc to cancel. Light + dark. |
| `python-editor-help-{light,dark}.png` | PYRUN-13, PYRUN-18 | Edit value sheet in Python mode with the F1 help popover open above the chip: the KEYBOARD list of shortcuts and their actions, the X close control at its top-right, and the Show tips toggle collapsed at the bottom. Light + dark. |
| `python-editor-help-tips-{light,dark}.png` | PYRUN-13, PYRUN-18 | Edit value sheet in Python mode with the help popover scrolled past the keyboard list to Hide tips and the tips expanded in their four subsections (Inputs, Outputs, Logging and Failure, and the fourth below the fold), each tip a one-line statement with a code sample. Light + dark. |
| `netcat-config-check-{light,dark}.png` | NETCAT-1, NETCAT-2, NETCAT-4, NETCAT-6, NETCAT-12 | Netcat config, Ports = Single, Mode = Check: Host, Ports, Port, Protocol TCP, Mode Check, Timeout 10; Failure Handling and Secrets collapsed. Light + dark. |
| `netcat-config-range-{light,dark}.png` | NETCAT-2, NETCAT-3 | Ports = Range: Port range `22, 80, 8000-8010`, Pass when One succeeds. Light + dark. |
| `netcat-config-talk-{light,dark}.png` | NETCAT-4, NETCAT-5, NETCAT-6 | Mode = Talk, Send = Text: Text, Timeout last of the top rows; Advanced expanded with CRLF line endings on, Close after sending off, Max reply size (bytes) 16777216, and the footer Line endings, closing and reply size for Talk. Light + dark. |
| `netcat-config-output-{light,dark}.png` | NETCAT-7 | OUTPUT tab: Success, Results, Reply with binding controls. Light + dark. |
| `ping-config-{light,dark}.png` | PING-1, PING-3, PING-6, PING-9 | Ping config as it opens: Host `10.0.2.2`, Count 4, Interval (seconds) 1, Packet size (bytes) 56, Timeout 30, Pass when Any reply, Log Output off; Advanced, Failure Handling and Secrets collapsed; OUTPUT VARIABLES carries Success, Summary and Replies. Light + dark. |
| `ping-config-pass-rate-{light,dark}.png` | PING-3 | Pass when At least X% replies, revealing Minimum rate (%) 75 directly beneath it; only that row differs from ping-config. Light + dark. |
| `ping-config-advanced-{light,dark}.png` | PING-7, PING-8 | Advanced expanded: IP version Auto, TTL empty, Don't fragment off, Source address empty; Failure Handling and Secrets still collapsed. Light + dark. |
| `sql-config-run-{light,dark}.png` | SQL-1, SQL-2, SQL-3, SQL-4, SQL-8, SQL-9, SQL-10 | SQL config as it opens: Operation Run SQL, Database type PostgreSQL, Host / Database / Username required and empty, Port placeholder 5432, Password secret, Script Type Source, SQL (Edit value) with the {} toggle, Parameters Edit..., Stop on error on, Timeout 300; TLS / Certificates open with the TLS toggle off and nothing under it, Advanced open with Connect timeout 30, Max rows 10000, Driver options Edit...; Failure Handling and Secrets collapsed; outputs Success, Rows, Row count, Rows changed; Save disabled with the generic note. Light + dark. |
| `sql-config-call-{light,dark}.png` | SQL-6, SQL-8 | Operation Call procedure: Procedure, Arguments Edit..., Out arguments (ordered list, Add argument) replace the script rows; TLS toggle on, revealing Verify Server Certificate, CA Certificate, Client Certificate and Client Key; outputs Success, Rows, Row count, Out values. Light + dark. |
| `sql-config-load-{light,dark}.png` | SQL-7, SQL-8 | Operation Load table: Table with Browse, Target table, Mode Add or replace revealing Key columns, Commit each batch on revealing Stop on error; Advanced open with Batch size 1000 among its rows; outputs Success, Rows changed. Light + dark. |
| `sql-config-field-errors-{light,dark}.png` | FIELDERR-1, FIELDERR-2, FIELDERR-3 | The Run SQL sheet with Host and SQL empty and required, Port 70000 and Timeout 0 out of range, each with the destructive border and its message under the field while label, type and toggle keep their alignment; Username in expression mode reading `usr` with an amber underline and an amber warning; the generic Save note. Light + dark. |
| `sql-editor-suggest-tables-{light,dark}.png` | SQL-10, SQL-11, SQL-12 | Edit value sheet in SQL mode with the cursor after FROM and nothing loaded: the suggestion list opens with a TABLES section holding only Get tables from the database; footer Kind Literal, Format SQL locked, F1 Help, Get Tables chip, Close / Save / Run. Light + dark. |
| `sql-editor-tables-{light,dark}.png` | SQL-12 | The Tables popover open from the footer chip: a search box with `ord` typed, `orders` and `order_items` with their columns under each, `orders` highlighted; the chip reads Tables · 14 with the refresh button beside it. Light + dark. |
| `sql-editor-suggest-params-{light,dark}.png` | SQL-3, SQL-10, SQL-11 | The cursor after `:` opens a PARAMETERS section listing the Parameters entries; the validation strip carries two amber warnings, an unused parameter and a script ending on SET search_path, with the amber underline on that line. Light + dark. |
| `sql-editor-running-{light,dark}.png` | SQL-13 | Run pressed: a spinner and a destructive Stop button with a square icon replace Run; Save disabled while it runs. Light + dark. |
| `sql-editor-get-tables-states-{light,dark}.png` | SQL-12 | The footer chip in its six states in order: Get Tables; Connecting... with Stop; Getting tables... with Stop; Got 14 tables with a checkmark; Tables · 14 with the refresh button; Could not get tables. Light + dark. |
| `opensearch-config-search-{light,dark}.png` | OS-1, OS-2, OS-3, OS-4, OS-5, OS-6, OS-8, OS-11 | OpenSearch config in Mode = Search, the header glyph SearchCode: Cluster URL and Index pattern required and filled, From `15 minutes ago` and To `now` with the clock glyph, Query language DQL, Query (Edit value), Mode Search, Fields (ordered list @timestamp, log.level, message, Add field), Max results 10000, Timeout 300; every row but the Query language and Mode selects carries the {} toggle; Sort, Authentication, TLS / Certificates, Advanced, Failure Handling and Secrets collapsed; outputs Success, Results, Total results. Light + dark. |
| `opensearch-config-aggregate-{light,dark}.png` | OS-1, OS-7, OS-8 | The same sheet with Mode = Aggregate: Group by time Every 1 minute, Group by field `No field`, Top values 10 and Stats (ordered list: Count, then `95th percentile of latency_ms` cut by the entry width, Add stat) replace Fields, Max results and the Sort group; outputs unchanged at Success, Results, Total results. Light + dark. |
| `opensearch-config-auth-advanced-{light,dark}.png` | OS-2 | Mode = Search with Authentication and Advanced open: Username `wave-qa`, then Password, API Key and Bearer Token as sealed secrets with the lock glyph, and the group footer `How WAVE identifies itself to the cluster: a username and password, an API key, a bearer token, or none. A client certificate under TLS / Certificates can go with any of them.`; Advanced holds Time field `@timestamp` and Connect timeout 30; Sort, TLS / Certificates, Failure Handling and Secrets collapsed. Light + dark. |
| `opensearch-time-picker-{light,dark}.png` | OS-4 | The From popover in two tabs side by side, each under its open trigger: Relative (15, minutes ago, Round to the minute unticked, `now-15m` underneath) and Absolute (the September 2026 calendar with the 25th selected, Time 10 : 42 : 05, the typed timestamp `2026-09-25T10:42:05Z`); the tab strip reads Absolute, Relative, Now. Light + dark. |
| `opensearch-stat-popover-{light,dark}.png` | OS-7 | The popover of the second Stats entry under its open trigger (`95th percentile of latency_ms`, cut by the entry width): Stat Percentile, Percent 95, Field latency_ms, and the column name line `percentile 95 of latency_ms`. Light + dark. |
| `opensearch-editor-dql-{light,dark}.png` | OS-5, OS-12, OS-13 | Edit value sheet in DQL mode, Kind Template: three lines with DQL coloring and `{{ svc }}` in the placeholder color; the cursor after `service.` opens a FIELDS list (service.name, service.version, service.environment, each `keyword`); `log.levle` carries the amber underline and the check strip reads `Unknown field log.levle in filebeat-*`; footer F1 Help, Fields · 214 with the refresh button, Close / Save / Run. Light + dark. |
| `opensearch-editor-get-fields-states-{light,dark}.png` | OS-12, OS-13 | The footer chip in its five states in order: Get fields; Getting fields... with Stop; Got 214 fields with a checkmark; Fields · 214 with the refresh button; Could not get fields. Light + dark. |
| `profiles/opensearch-profile-config-{light,dark}.png` | OS-15 | The Create Profile modal with Type = opensearch: nine parameter rows, none required - url (filled), username, password (secret), api_key (secret), bearer_token (secret), verify_ssl (true), ca_cert, client_cert, client_key (secret); no host, port, use_ssl, index or timeout. Light + dark. |
| `sftp-config-upload-{light,dark}.png` | SFTP-2, SFTP-4, SFTP-5, SFTP-8 | SFTP config as it opens, the header glyph FolderSync: Session ID `ssh_session` required, Operation = Upload, Source `testdata://orders.csv` required with Browse, Destination `/inbound/orders.tmp` required, If the file exists = Replace it; Advanced, Failure Handling and Secrets collapsed; outputs Summary = Table, Success. Light + dark. |
| `sftp-config-download-{light,dark}.png` | SFTP-4, SFTP-5, SFTP-6, SFTP-8, SFTP-10 | Operation = Download: Source `/outbound/orders.out` required, Destination optional and empty with Browse, If the file exists = Replace it; Advanced expanded with Timeout 300, Max size (MiB) 1024 and Max files 10000, the group footer reading "Limits for this block"; outputs unchanged. Light + dark. |
| `sftp-config-list-{light,dark}.png` | SFTP-3, SFTP-9 | Operation = List: Path `/outbound/*.out` required, Include subfolders unticked; Advanced collapsed; outputs Entries = Table, Count = Integer, Success. Light + dark. |

---

### details/

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `suite-detail.png` | SUITE-1 through SUITE-25 | Definition view: metadata panel, tests table, variable manager |
| `regression-detail.png` | REG-1 through REG-22 | Definition view: suites table with Tests column |
| `suite-execution-detail.png` | EXEC-1 through EXEC-24 | Runtime view: immutable, console with output |
| `regression-execution-detail.png` | REG-EX-1 through REG-EX-25 | Runtime view: suites table with status |
| `function-detail-light.png` | FNDETAIL-1 through FNDETAIL-14 | Function detail page (resting / Changelog expanded): grouped major version nav, per-version metadata header, collapsible sections. Light. |
| `function-detail-dark.png` | FNDETAIL-1 through FNDETAIL-14 | Same, dark theme. |
| `function-detail-expanded-light.png` | FNDETAIL-7 through FNDETAIL-10 | All sections expanded: Changelog, Details (scrollable Markdown), Inputs/Outputs (with Description), Usage (Tests + Functions). Light. |
| `function-detail-expanded-dark.png` | FNDETAIL-7 through FNDETAIL-10 | Same, dark theme. |

---

### modals-build/

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `suite-create-edit.png` | FORM-1 through FORM-19 | Create and Edit modals side by side |
| `suite-delete.png` | FORM-20 through FORM-30 | Simple and Enhanced delete confirmations |
| `regression-create-edit.png` | FORM-31 through FORM-38 | Create, Edit, and Delete modals |
| `regression-run.png` | LISTRUN-1 through LISTRUN-12 | Run modal with environment selection |
| `save-validation-path-rows-light.png` | CANVAS-215 through CANVAS-218 | Save-validation dialog with path-aware error rows (`Func_1 / Func_2 / Leaf - <message>`), clickable segments that drill-and-focus, scope-aware body-reference wording, and the missing-version Shared row. Light theme. |
| `save-validation-path-rows-dark.png` | CANVAS-215 through CANVAS-218 | Same as above, dark theme. |
| `publish-outcome-light.png` | CANVAS-219 through CANVAS-222 | Edit-mode publish three-option confirmation modal: upload icon + "Publish a new version?" + version-transition line, body paragraph, note box (Set New / Keep Old semantics), and a single-row footer (`Cancel` / `Publish and keep Old` / `Publish and set New`). No save-status line; identical in both modes. Light theme. |
| `publish-outcome-dark.png` | CANVAS-219 through CANVAS-222 | Same as above, dark theme. |
| `entity-picker-paginated-light.png` | PICKER-1, PICKER-2, PICKER-3, PICKER-5 | Shared EntityPickerModal (Add Tests to Suite / Add Suites to Regression): paginated list with the floating bottom-center "Loading…" pill and the "{total} {entity} - refine your search to narrow down" status line below the list. Light theme. |
| `entity-picker-paginated-dark.png` | PICKER-1, PICKER-2, PICKER-3, PICKER-5 | Same paginated picker, dark theme. |
| `entity-picker-error-light.png` | PICKER-4 | Shared EntityPickerModal error state: alert icon + "Unable to load {entity}" + "Try Again" replacing the list when a fetch fails. Light theme. |
| `entity-picker-error-dark.png` | PICKER-4 | Same error state, dark theme. |

---

### lists-library/

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `profiles-list-populated.png` | PROFILE-1 through PROFILE-10 | Profiles table with Environments, Usage columns |
| `blocks-list-populated.png` | BLOCK-1 through BLOCK-10 | Blocks table with Version, Author, Usage |
| `plugins-list-populated.png` | PLUGIN-1 through PLUGIN-10 | Plugins table with Category (not Tags) |
| `functions-list-populated.png` | FNLIST-1 through FNLIST-10 | Functions library table: Name (+ description), Tags, Version pill, Updated, Actions; Import toolbar, no New affordance |
| `function-import-collision-review-light.png` | FNLIST-12 | Import dialog review step: OK / name-conflict / ID-collision / blocked rows. Conflict rows show a muted reason sub-line; Auto-rename default. Light. |
| `function-import-collision-review-dark.png` | FNLIST-12 | Same review step, dark theme. |

---

### utility/

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `settings-page.png` | SETTINGS-1 through SETTINGS-16 | Two-column layout, Environments table |
| `settings-general-{light,dark}.png` | SETTINGS-14, SETTINGS-18, SETTINGS-19, SETTINGS-20, SETTINGS-22 | Settings > General with nothing changed: Cancel and Save faded on the Logging heading line; one subtitle per section; label-only Log Level and Time Zone rows; Secret Masking |
| `settings-general-staged-{light,dark}.png` | SETTINGS-18 | General with a change waiting for Save: Cancel and Save enabled; a masking switch on |
| `mcp-server-section-{light,dark}.png` | MCP-1 through MCP-9 | Superseded by `mcp-server-save-{light,dark}.png` and `mcp-server-save-running-{light,dark}.png`; kept for reference, it does not govern the design. Settings > MCP Server section: status bar (Running dot, endpoint URL + copy, clients count, last activity), Enablement (persistent + until-restart instant switches), Endpoint group staged behind Cancel/Apply (port, bind scope, Require authentication, username, write-only sealed password), Sessions rows (client, IP, connected/active, Disconnect), scrollable Recent Activity feed |
| `mcp-apply-confirm-{light,dark}.png` | MCP-5, MCP-6 | Superseded by `mcp-save-confirm-{light,dark}.png` and `mcp-save-confirm-exposure-{light,dark}.png`; kept for reference, it does not govern the design. Apply-endpoint-changes confirmation: restart warning body + amber network-exposure warning block (shown only when bind scope changes to Network), Cancel / "Apply and restart" |
| `mcp-server-save-{light,dark}.png` | MCP-3, MCP-4, MCP-7, SETTINGS-18, NET-11 | Settings > MCP Server, endpoint stopped: "Enable MCP server" staged on, a new password with the score "Weak", Cancel and Save enabled on the "MCP Server" heading line, no footer bar |
| `mcp-server-save-running-{light,dark}.png` | MCP-3, MCP-4, MCP-7 | MCP Server, endpoint running: "Active" cue on the saved mode, a new password with the score "Very strong" |
| `mcp-server-password-saved-{light,dark}.png` | MCP-7 | MCP Server with a saved password in the masked field |
| `mcp-save-confirm-{light,dark}.png` | MCP-5 | Confirmation "Save MCP server changes?" with the restart sentence and "Save and restart" |
| `mcp-save-confirm-exposure-{light,dark}.png` | MCP-6 | The same confirmation on a stopped endpoint: the exposure warning only, confirm "Save" |
| `mcp-see-connection-{light,dark}.png` | SESS-4 | See connection destination: Settings > MCP > Sessions scrolled to and highlighting the target client (violet ring + "From your workbench" chip), Disconnect beside it |
| `wave-server-section-{light,dark}.png` | WSRV-1 through WSRV-8 | Settings > WAVE Server section: two read-only server fact cards (Frontend + Backend Server, each with running status, copyable reachable addresses, and lock-marked Port + Bind scope), then the live Sessions roster (identity = browser + OS, IP, connected/active, Disconnect) with the admin's own row marked "You" and Disconnect Others / Disconnect All at the section header. No enablement, no staged apply, no activity feed |
| `wave-server-see-connection-{light,dark}.png` | WSRV-9 | Person-holder See connection destination: Settings > WAVE Server > Sessions scrolled to and highlighting the holder's browser session (accent ring + "From your workbench" chip) with Disconnect beside it, the admin's own row still marked "You" below |
| `wave-server-data-folder-{light,dark}.png` | WSRV-10 | Settings > WAVE Server, Backend Server card with the lock-marked, read-only Data folder row (absolute path, copy button) beside the existing Port and Bind scope facts. The card's rows are superseded by `wave-server-config-file-{light,dark}.png`; the Data folder row is unchanged |
| `wave-server-config-file-{light,dark}.png` | WSRV-11 | Settings > WAVE Server, Backend Server card with the Config file row under Data folder |
| `network-ssh-hosts-{light,dark}.png` | NET-1, NET-2, NET-3, NET-11 | Settings > Network > SSH Hosts, unlocked: Network group open in the section nav, Cancel / Save header, Host Key Policy (Lock trusted hosts off, Default block action Accept New (a saved value; the default is Disabled, NET-2)) with controls centered against their help lines, Trusted SSH Hosts table (Host, Port, Key type, Fingerprint, Added; trash per row) with search, Mass Action and Add hosts, pagination |
| `network-ssh-hosts-locked-{light,dark}.png` | NET-2, NET-3 | SSH Hosts with Lock trusted hosts on: Default block action switched to Strict, Accept New shown disabled, Save enabled by the staged change |
| `network-add-hosts-detect-{light,dark}.png` | NET-4 | Add Hosts dialog, Detect from host: Host, Port, Detect; found keys with checkboxes, Key type and full SHA-256 fingerprints, one key marked "Already trusted" with its checkbox disabled; Cancel / Add |
| `network-add-hosts-paste-{light,dark}.png` | NET-4 | Add Hosts dialog, Paste lines: known_hosts lines in the plain-text editor with line numbers; preview rows (Host, Key type, Fingerprint), a multi-name line as one row; the bad line listed under the table as `Line {n}: {reason}` in the error text color |
| `network-certificates-{light,dark}.png` | NET-1, NET-5, NET-7, NET-9 | Settings > Network > Certificates, built-in source: Public Certificate Authorities option cards (WAVE's built-in list selected), read-only Built-in Authorities table (Name, Organization, Expires, eye icon), Additional Certificates table (Name, Type, Expires; eye and trash per row) with search, Mass Action and Add certificate |
| `network-certificates-host-store-{light,dark}.png` | NET-6, NET-7 | Certificates with This WAVE host's store selected: lock-marked WAVE Host's Store summary (Store, Certificates, Last changed) in place of the Built-in Authorities table, Additional Certificates below |
| `network-certificate-view-{light,dark}.png` | NET-9 | Certificate dialog: Subject, Issuer, Type, Path length, validity with status badge, SHA-256 fingerprint with copy, Serial number, Key, Signature algorithm, Key usage, key IDs, read-only PEM with Copy; corner X and Close |
| `network-add-certificate-{light,dark}.png` | NET-8 | Add Certificate dialog: PEM text area, compact one-row file drop zone, preview table (Name, Type, Expires) with an expired certificate badged and still checked, and one marked "Already added" with its checkbox disabled; Cancel / Add |
| `network-proxy-off-{light,dark}.png` | NET-10, NET-11 | Proxy Setup, off: the line under the title, only Use a proxy in the card, Cancel and Save faded |
| `network-proxy-host-{light,dark}.png` | NET-10, NET-11 | Proxy Setup, on, Source WAVE host's settings: HTTPS_PROXY, HTTP_PROXY and NO_PROXY read-only and lock-marked |
| `network-proxy-custom-{light,dark}.png` | NET-10, NET-11 | Proxy Setup, on, Source Custom, drawn as the whole Settings page: the menu with Network > Proxy > Setup active and Blocks under it; IP or Hostname, Port, Username, the saved Password in the masked field, Use the proxy for, the address list with Exact and Regex rows and Add, Use the proxy for local addresses too; Save enabled |
| `network-proxy-custom-invalid-{light,dark}.png` | NET-10 | Proxy Setup, Custom, with invalid input: one field and three list rows with the error border and their messages under them, Save disabled |
| `network-proxy-blocks-{light,dark}.png` | NET-10 | Proxy Blocks, drawn as the whole Settings page with Blocks active in the menu: the first two sections open, Not applicable closed; blocks in their palette groups and colors |
| `network-proxy-blocks-open-{light,dark}.png` | NET-10 | Proxy Blocks with Blocks that use this proxy closed and Not applicable open |
| `backup-schedule-{light,dark}.png` | SETTINGS-21, SETTINGS-18 | Periodic Backup on with a change waiting for Save: Cancel and Save on its heading line, `~/wave-backups`, no Save Schedule button. |
| `backup-parts-{light,dark}.png` | BACKUP-1 | Create Backup with the nine-part list: Tests, Environments, Profiles / Suites, Regressions, Functions / System Variables, SSH Hosts, Additional Certificates; no disabled entry |
| `backup-restore-preview-{light,dark}.png` | BACKUP-2, BACKUP-3, BACKUP-5, BACKUP-6, BACKUP-7, BACKUP-9 | Restore preview: nine parts, the last count column `Errors`; Tests open with its fatal entry first, leading with `Cannot be restored.`, and its conflicts under it; the list is as high as six one-line entries, then it scrolls; Profiles and Functions closed with a chevron |
| `backup-restore-result-{light,dark}.png` | BACKUP-4, BACKUP-6, BACKUP-7, BACKUP-9 | Restore Complete: one line per part, Tests counted as `8 imported, 9 skipped, 1 failed` and open with its fatal entry, leading with `Not restored.`, and its skipped entries |
| `backup-restore-overwrite-confirm-{light,dark}.png` | BACKUP-8 | Restore with Overwrite and a conflict in a ticked part: the shared confirmation dialog `Overwrite conflicting entities?` with Cancel and Overwrite, over the dimmed preview |
| `tooltip-surface-{light,dark}.png` | SHELL-7, SHELL-7a through SHELL-7d | The one shared tooltip applied product-wide: outlined menu-family chip with its arrow, over the canvas and over a panel, with and without a key badge, plus the wide wrapping variant. Replaces the primary-accent chip and the four other tooltip mechanisms that existed alongside it. Both themes. |

In the Settings frames a second, lighter line sits beside the divider between the section list and the page; it is not part of the design (SETTINGS-5).

---

### canvas-node/ (light + dark pairs)

Canonical wireframes for the canvas-block visual (header + persistent status bar architecture). Same markup in both modes; theme tokens switch via WAVE design system. Reference for plugin / control / function / note blocks.

**Title labels in these wireframes (`HTTP_Client`, `If_Else`, `For_Each`, ...) are placeholders meant to identify the entity kind, not the rendered string.** Per § 15.4.8 of `04-visual-workflow-builder.md`, the canvas title is the human-readable display name supplied by the registry (e.g. "HTTP Client", "If/Else", "For Each"). Snake_case / camelCase / kebab-case forms are reserved for the entity's internal id and never appear in the title row.

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `00-overview-light.png` | NODE-1 through NODE-12 | Full overview of the block design (anatomy + idle matrix + run states + note exception). Light mode (`#FAFAFA` page, `#FFFFFF` card). |
| `remote-execution.png` | REMEX-1 through REMEX-4 | Remote Execution container block (For-Loop-style: input + cyan body sub-flow "runs on the Execution Host" + then) and its config (mandatory Execution Host, single Remote Session ID output) |
| `block-icon-tooltips-{light,dark}.png` | CANVAS-238 through CANVAS-240, SHELL-7 | Action-cluster tooltips anchored below their button: Configure / `Enter` on a plugin-control block, More options / pointer right-click and Open / `Ctrl+Enter` on a Function block. One tooltip per block so they do not collide; in the app only the hovered icon shows one. Both themes. |
| `00-overview-dark.png` | NODE-1 through NODE-12 | Same content, dark mode (`#09090B` page, `#0F0F12` card, `#FAFAFA` text). |
| `01-anatomy-light.png` | NODE-1, NODE-2, NODE-3 | Annotated examples: plugin (PASS, ver-update arrow visible) + Local Function (BP TR-corner + L badge + FAIL). Light. |
| `01-anatomy-dark.png` | NODE-1, NODE-2, NODE-3 | Same anatomy, dark. |
| `02-idle-matrix-light.png` | NODE-4, NODE-5 | 4x2 grid: each block type (plugin / control / fn-local / fn-shared) with and without description. Demonstrates body-height adaptation and empty status-bar behavior. Light. |
| `02-idle-matrix-dark.png` | NODE-4, NODE-5 | Same matrix, dark. |
| `03-run-states-light.png` | NODE-6 through NODE-10 | FAIL+alert / RUN (animated border pulse) / SKIP / Local Fn (BP+L+PASS) / DISABLED Shared / worst-case density (selection halo + BP + S + RUN + ver-arrow + 4-button action cluster). Light. |
| `03-run-states-dark.png` | NODE-6 through NODE-10 | Same run states, dark. |
| `04-note-exception-light.png` | NODE-11, NODE-12 | Note variant: amber theme, no handles, no cog, no dig-in. Slim status bar with kebab only. With and without description. Light. |
| `04-note-exception-dark.png` | NODE-11, NODE-12 | Same notes, dark (amber `#2A1D05` bg, `#78350F` border). |
| `05-note-edit-light.png` | NODE-12, NODE-13 | Note edit-mode: persistent slim status bar morphs from `[kebab]` to `[color picker | accept | cancel]`. Solid blue 2 px border replaces dashed amber while editing. Idle Note alongside for direct comparison. Light. |
| `05-note-edit-dark.png` | NODE-12, NODE-13 | Same Note edit-mode demonstration, dark. |
| `wait-until-node-{light,dark}.png` | WAIT-3, WAIT-5, WAIT-7 | Wait Until block in both modes plus its running state: Retry mode carrying a `retry` lane in the repeated-sub-flow blue and the always-present `then` lane in the container-exit neutral; Watch mode with `then` alone (Delay's shape); the running block. The third panel draws a countdown badge beside RUNNING that the product does not carry - a running Wait Until shows RUNNING alone (WAIT-7). Role legend below; no lane text labels (hover tooltip only). Both themes. |
| `switch-node-{light,dark}.png` | SWITCH-1, SWITCH-5, SWITCH-6, SWITCH-7 | Switch/Case container block carrying three case lanes, a default lane and the always-present `then` lane, with the role legend. Case lanes take the conditional orange, default the muted neutral, `then` the container-exit neutral; no lane text labels (hover tooltip only). Both themes. |
| `parallel-node-{light,dark}.png` | PARALLEL-1, PARALLEL-2 | Parallel container block at three branches and at the two-branch minimum, each carrying its branch lanes plus the always-present `then` join lane, with the role legend. Branch lanes take violet (a role no other lane uses), `then` the container-exit neutral; block widens by one lane slot per branch; no lane text labels (hover tooltip only). Both themes. |

Design decision IDs (NODE-*) are settled in the canvas node section of `design/03-component-design/`. Summary:
- **NODE-1**: Three-region card structure - top handle / body (icon + title + optional description) / persistent status bar at the bottom.
- **NODE-2**: Status bar always visible. Selection adds a dashed halo only; no chrome morph.
- **NODE-3**: Status bar layout - badges left, action cluster right. Right edge of action cluster anchored regardless of badge count.
- **NODE-4**: Body height adapts to whether description is set. No description -> title-only height; description -> 2-line clamp below title.
- **NODE-5**: Title is the user-set block title; description is an optional secondary line in muted text.
- **NODE-6**: Badges (left side) ordered: alert -> Local-or-Shared (Function only) -> run state.
- **NODE-7**: Function-state badges are single-letter L (Local, slate) and S (Shared, indigo) with hover tooltips.
- **NODE-8**: Run state badges - PASS (green) / FAIL (red) / SKIP (amber) / RUNNING (cyan + animated border pulse) / PAUSED (amber) / STOPPED (orange, user-halted before this block finished) / DISABLED (neutral; full-card grayscale + opacity 0.55).
- **NODE-9**: Action cluster (right side) ordered: ver-update arrow (when applicable) -> cog -> kebab -> dig-in (Function only).
- **NODE-10**: Version off the canvas. Lives in the configuration modal header; the new-version-available arrow in the action cluster is the only canvas surface that mentions versioning at all.
- **NODE-11**: Breakpoint marker is a 12px filled-red circle at TR corner of the body (not a status-bar badge). Validation alert remains in the status bar as a badge.
- **NODE-12**: Note exception - no top/bottom handles, no cog, no dig-in. Amber-themed body. Slim status bar with kebab only.
- **NODE-13**: Note edit-mode chrome morph (the single allowed deviation from NODE-2's no-morph rule). Entering edit mode (double-click body or kebab > Edit) swaps the slim status bar's contents from `[kebab]` to `[color picker]` (left) + `[accept] [cancel]` (right), and replaces the dashed amber border with a solid 2 px blue border. Leaving edit mode (accept, cancel, Escape) restores the idle chrome. The bar itself stays visible in both states; only its contents and the body border change.

---

### function-canvas/ (light + dark pairs)

Wireframes for the Function drill-down and schema-editor surfaces. Extends the existing canvas breadcrumb and Variable Manager (`workbench/vmgr-panel.png`) with Function-scoped behavior.

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `01-var-mgr-grouped-light.png` | FN-VMGR-1 through FN-VMGR-5 | Variable Manager inside a drilled-in local Function. Same chrome / filter / sort as today. Adds collapsible PARAMETERS group with INPUTS / OUTPUTS sub-separators, plus the existing VARIABLES group. IN / OUT row badges. "+ Add ▾" dropdown shows Input parameter / Output parameter / Variable. Light. |
| `01-var-mgr-grouped-dark.png` | FN-VMGR-1 through FN-VMGR-5 | Same, dark. |
| `02-breadcrumb-states-light.png` | FN-BC-1 through FN-BC-4 | Canvas breadcrumb extended with Function drill segments. Three states: not drilled (no Function segments), one level deep (`Suite / Test / Function_1`), two levels deep (`Suite / Test / Function_1 / Helper_2`). Function segments in violet (`#a78bfa`) with `ƒ` icon. Light. |
| `02-breadcrumb-states-dark.png` | FN-BC-1 through FN-BC-4 | Same three states, dark. |
| `04-param-array-enum-light.png` | FN-PARAM-5, FN-PARAM-6 | Array enum mechanism. Two states side by side: Type=Array with Create enum unchecked (today's array editor), and Type=Array with Create enum checked. When checked: a Value Type sub-field appears directly below Type; the same Default Value array editor holds the allowed-values literal; expression-mode toggle is disabled; in Input mode the Required flag is locked on (still rendered as a uniform checkbox row, just disabled-and-checked). Light. Superseded by VMGR-98 / VMGR-100 and VMGR-112. |
| `04-param-array-enum-dark.png` | FN-PARAM-5, FN-PARAM-6 | Same two states, dark. Superseded by VMGR-98 / VMGR-100 and VMGR-112. |

---

### function-lifecycle/ (light + dark pairs)

Wireframes for the Function publish / detach / inspect / library surfaces. Lifecycle metadata (Version, Changelog, Details) is captured at publish time and surfaced read-only on the Published config-modal variant.

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `publish-dialog-light.png` | FN-LC-1 through FN-LC-5 | Publish Function dialog. Single-mode form. Row 1: Name (free-form display label, 32-char cap with `N / 32` counter) + Version (`1.0.0`). Description, Tags (chip input), Changelog, Details below full-width. Footer: left-aligned note "A new library Function will be created." + Cancel + Publish. Light theme. |
| `publish-dialog-dark.png` | FN-LC-1 through FN-LC-5 | Same dialog, dark theme. |
| `library-modal-populated-light.png` | FN-LC-6, FN-LC-7, FN-LC-8 (plus CANVAS-204, CANVAS-205, CANVAS-206) | Functions Library modal in populated state. Non-blocking, draggable header (CANVAS-204). Toolbar: search input + "Tags ▾" popover (single WAVE-pattern button, NOT a chip strip). Card grid: responsive `auto-fill, minmax(220px, 1fr)` columns; cards are drag sources. Card body: icon + name on row 1, 1-line description on row 2, tag chips on row 3 (no S badge). Light theme. |
| `library-modal-populated-dark.png` | FN-LC-6, FN-LC-7, FN-LC-8 (plus CANVAS-204, CANVAS-205, CANVAS-206) | Same modal, dark theme. |
| `config-modal-profiles-local-light.png` | FN-LC-9, FN-LC-10, FN-LC-11 (amends CANVAS-214) | Function instance config modal, Local variant, with the new Profiles button in the footer-left. Body unchanged from CANVAS-207..213. Footer: `Profiles` (blue-outlined, count badge when bindings exist) + Cancel + Save. Light theme. |
| `config-modal-profiles-local-dark.png` | FN-LC-9, FN-LC-10, FN-LC-11 (amends CANVAS-214) | Same, dark theme. |
| `config-modal-profiles-published-light.png` | FN-LC-9, FN-LC-10, FN-LC-11 (amends CANVAS-214) | Function instance config modal, Published variant, with the new Profiles button in the footer-left. Body unchanged. Footer: `Changelog + Details + Profiles` (blue-outlined) + Cancel + Save. Light theme. |
| `config-modal-profiles-published-dark.png` | FN-LC-9, FN-LC-10, FN-LC-11 (amends CANVAS-214) | Same, dark theme. |
| `readonly-action-bar-light.png` | FN-LC-12, FN-LC-13, FN-LC-14 | Read-only inspect chrome on the workbench top action bar. Inserted between the Env selector and the existing env-icon / Debug / Run cluster: vertical splitter, "🔒 Read-only" pill (indigo, uppercase), Edit button (default outline style), vertical splitter. Visible only when drilled into a Published Function. Light theme. |
| `readonly-action-bar-dark.png` | FN-LC-12, FN-LC-13, FN-LC-14 | Same, dark theme. |
| `make-local-kebab-light.png` | FN-LC-15 | Kebab (and right-click context menu) on a Published Function. New entries `Open` + `Make Local…` at the top of the menu as a lifecycle group, separated from the run / debug / clipboard / state / delete groups by a divider. Light theme. |
| `make-local-kebab-dark.png` | FN-LC-15 | Same, dark theme. |
| `make-local-confirm-light.png` | FN-LC-16, FN-LC-17 | "Make Local" confirmation dialog. Title + close, prose explaining the deep-copy and the loss of upstream link, an amber callout reinforcing "library entry not modified", Cancel + Make Local (primary blue) footer. Light theme. |
| `make-local-confirm-dark.png` | FN-LC-16, FN-LC-17 | Same, dark theme. |

Design decision IDs (FN-LC-*) for this set are recorded in `00-design-decisions.md`:
- **FN-LC-1**: Function display name accepts any printable keyboard character (letters, digits, spaces, punctuation), capped at 32 characters. Uniqueness against the library is checked case-insensitively. The canonical identifier is a UUID assigned by the backend and never shown in the publish dialog UI.
- **FN-LC-2**: Version is a semver string. The publish dialog's Version field starts at `1.0.0` and takes any valid semver; Edit-mode publishing picks the version from a bump-target dropdown (FN-VER-4).
- **FN-LC-3**: Description, Tags, Changelog, and Details are first-class library-entry fields. Description pre-fills from the local Function's description on the originating canvas. Tags are blank on first publish (local Functions don't carry tags). Changelog is optional for the initial release and required for any subsequent version (enforced on edit-mode publish, FN-VER-7). Details has no required state.
- **FN-LC-4**: The publish dialog footer carries a left-aligned plain-text note describing the outcome ("A new library Function will be created.") next to the Cancel + Publish actions. No banner, no top sub-description.
- **FN-LC-5**: On confirm: the dialog closes, the Function Block on the canvas it sits in swaps from the L (local) badge to the S (shared) badge, and a toast confirms the publish. No multi-step confirmation screen.
- **FN-LC-6**: Functions Library modal card grid is responsive: `grid-template-columns: repeat(auto-fill, minmax(220px, 1fr))`. Columns are added as the user resizes the modal; the minimum is one column. The modal itself remains draggable and non-blocking per CANVAS-204.
- **FN-LC-7**: Tag filtering inside the Functions Library modal reuses the existing WAVE `EntityFilters` tag-popover pattern (`frontend/src/components/shared/filters/entity-filters.tsx`): a single h-9 / w-[120px] button rendered as "Tags ▾" when no filter is active and "N tags" with accent border when one or more tags are selected. Clicking opens a popover with a search input and a multi-select checklist of all library tags. "Clear Filters" appears next to the tag button in the WAVE warning-toned outline style only when filters are active. No tag-chip strip is rendered in the toolbar.
- **FN-LC-8**: Library card composition: icon (Function `ƒ` glyph in monospace italic, identical to the on-canvas Function block icon) + name (bold, single-line ellipsis) on row 1; 1-line description (truncated with ellipsis) on row 2; tag chips on row 3. The S lifecycle badge is NOT rendered on library cards because the whole modal is the library (= always shared) and the badge would be redundant. Each card is a drag source; drag-end on the canvas materializes a published Function reference at the drop position.
- **FN-LC-9**: The Function instance config modal carries a Profiles button on BOTH Local and Published variants, reusing the existing plugin/control "Profiles" affordance (PROFILE-11) verbatim (same blue-outlined button, same count badge, same `ProfileBindingModal` target). This amends CANVAS-214's "Profiles button is never shown on a Function modal regardless of variant" exclusion.
- **FN-LC-10**: Profile binding is per-instance, not on the library entry. The same published Function dropped into two different Tests can carry different profile bindings. The library record stores no default profile.
- **FN-LC-11**: Footer placement: Profiles sits in the left button group. Local variant: `Profiles + Cancel + Save` (no Changelog or Details because Local Functions have no library-version history). Published variant: `Changelog + Details + Profiles + Cancel + Save` (Profiles slotted after Details so the version-related buttons stay grouped).
- **FN-LC-12**: Read-only inspect chrome lives in the workbench top action bar, NOT in the canvas breadcrumb bar. The chrome appears only when the user is drilled into a Published Function (hidden on the test canvas and inside Local Functions). Layout, left-to-right within the action bar: Env selector | vertical splitter | "🔒 Read-only" pill | Edit button | vertical splitter | existing env-icon | Debug | Run.
- **FN-LC-13**: The Read-only pill uses the indigo S-badge palette (`bg-indigo-500/15`, `text-indigo-600` / dark `text-indigo-300`) with a lock glyph and the literal copy "Read-only" in uppercase. The pill is decorative (no click action); the actual read-only enforcement happens in the canvas store.
- **FN-LC-14**: The Edit button uses the default outline-button style and a pencil glyph. It opens Edit mode (per-Test draft + semver-target selection). The button is never disabled.
- **FN-LC-15**: "Make Local" and the restored "Open" entry sit at the top of the Published-Function kebab as a lifecycle group, separated from the run / debug / clipboard / state / delete groups by a divider. The same two entries appear in the right-click context menu in the same order. "Make Local" carries a trailing ellipsis to signal it opens a confirmation dialog. Local Functions do NOT carry a "Make Local" entry (already local) and they continue to render the existing "Open" entry as today.
- **FN-LC-16**: "Make Local" opens a confirmation dialog (NOT a silent fork). Body: a one-paragraph prose explanation that names the Function being detached (monospace pill) and states the loss of upstream link, plus an amber callout reinforcing that the library entry is not modified and that re-attaching is achieved by re-dropping from the library. Footer: Cancel + Make Local (primary blue). On confirm: backend deep-copies the published definition into the Test's storage as local content; the canvas block visual swaps S→L; a toast confirms.
- **FN-LC-17**: The confirmation dialog is reused for both the kebab trigger and the right-click context menu trigger (single component, single state). Closing via Cancel is a no-op; Escape and a click outside do not close the dialog. Closing via Make Local triggers the detach service call and then closes the dialog only on success; on failure the dialog stays open and surfaces the inline error returned by the service.

---

### function-versioning/ (light + dark pairs)

Wireframes for the Function multi-version + edit-mode surfaces. Edit mode introduces a per-Test mutable draft on top of a Published reference, surfaced by a red SVG asterisk on the S badge. The edit-mode publish flow reuses the publish-to-library modal shell but swaps the Version input for a smart bump-target dropdown with live validators.

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `edit-mode-badge-light.png` | FN-VER-1, FN-VER-2 | Function canvas block, Published variant, in edit mode. The existing S badge is unchanged (indigo); a small red SVG asterisk is overlaid with its geometric center on the badge's top-right corner via `top:0; right:0; transform: translate(50%, -50%)`. The asterisk is a stroked SVG path (not a text glyph) so its visible center is reliably centered in its 14×14 wrapper box; a 3-layer drop-shadow halo (white in light, ink in dark) preserves legibility against the indigo fill. Shown in two states: resting (no hover) and hovered (tooltip open). Tooltip is shadcn-style, dark popover in light theme / inverted in dark, with a "Edit-mode draft" title and a body explaining unpublished changes on top of v1.2.0 plus the kebab-publish / kebab-drop affordances. Light theme. |
| `edit-mode-badge-dark.png` | FN-VER-1, FN-VER-2 | Same, dark theme. |
| `publish-edit-mode-clean-light.png` | FN-VER-3, FN-VER-4, FN-VER-6, FN-VER-7, FN-VER-8 | Edit-mode publish modal in the clean case (description-only draft against v1.4.2, MINOR is the auto-derived bump target, all bump options would be enabled in the dropdown). Locked target chip at top (`ValidateUser · from edit mode · source v1.4.2`). Version field is a smart dropdown showing the auto-selected `1.5.0` with a color-coded `minor` chip (amber); the trigger summarizes the current selection. Description / Tags / Details pre-fill from source and are editable. Changelog is mandatory (`*` red asterisk) - Publish button is disabled (visibly grayed) until a changelog entry is provided. Footer: Cancel + Publish 1.5.0 (disabled). Light theme. |
| `publish-edit-mode-clean-dark.png` | FN-VER-3, FN-VER-4, FN-VER-6, FN-VER-7, FN-VER-8 | Same, dark theme. |
| `publish-edit-mode-violations-light.png` | FN-VER-3, FN-VER-4, FN-VER-5, FN-VER-6, FN-VER-7, FN-VER-8 | Edit-mode publish modal in the violator case (Var Manager added a REQUIRED input `tenant_id` to the draft body). Version dropdown is open: PATCH (`1.4.3`) and MINOR (`1.5.0`) options are disabled with `(i)` info icons; hovering MINOR's `(i)` opens a tooltip ("MINOR cannot add a REQUIRED input. Make tenant_id optional, or bump to MAJOR.") - wireframe shows the MINOR tooltip statically as the demonstration. MAJOR (`2.0.0`) is selected and the trigger's bump chip is red. Custom field below the divider has been typed `1.4.3`, surfaces inline live-validation error in red ("1.4.3 is a PATCH bump - incompatible with the current draft..."). Trigger has a red outline + faint red ring to signal the major-target state. Changelog filled in - Publish enabled. Light theme. |
| `publish-edit-mode-violations-dark.png` | FN-VER-3, FN-VER-4, FN-VER-5, FN-VER-6, FN-VER-7, FN-VER-8 | Same, dark theme. |
| `missing-version-node-light.png` | FN-VER-9, FN-VER-10 | Function canvas block referencing a Published Function at a version that is no longer in the library. Reuses the existing red-triangle validation alert (node-validation-alert.tsx) to the left of the S badge - same visual treatment as any other blocking validation error. Shown in two states: resting (just the alert + S badge) and hovered (tooltip "Missing version - Pins v1.4.2, not in library. Open config to pick another version."). Light theme. |
| `missing-version-node-dark.png` | FN-VER-9, FN-VER-10 | Same, dark theme. |
| `missing-version-modal-light.png` | FN-VER-9, FN-VER-11 | Non-edit-mode Published config modal opened on a missing-version instance. Red destructive banner at top names the missing version + recovery path (just "Pick an available version from the dropdown."). Version field trigger has a red border + faint red ring; the missing version text is rendered in strikethrough with a destructive `Missing` chip. Dropdown open: lists only the available library versions (no "Currently pinned" section - the missing version is already surfaced in the trigger and banner). Per-row order: version, date, optional `latest` chip. Save is the recovery action once the user picks a valid version. Light theme. |
| `missing-version-modal-dark.png` | FN-VER-9, FN-VER-11 | Same, dark theme. |
| `library-card-version-pill-light.png` | FN-VER-12, FN-VER-13 | Library card with version pill. Row 1: `f-icon + name`, name takes the full row width and truncates with ellipsis (hover → tooltip with full name). Row 2: description (truncated). Row 3: tags clipped to fit + `(+N)` overflow chip + version pill anchored bottom-right via flex `justify-content: space-between`. Hover the `(+N)` chip → tooltip with the full tag list. Version pill is mono-font indigo (matches S-badge palette), no count badge - keep it minimal. Two cards stacked: resting (short name, 2 tags, no truncation) + both-tooltips-visible (long name truncated, `+4` tag overflow). Light theme. |
| `library-card-version-pill-dark.png` | FN-VER-12, FN-VER-13 | Same, dark theme. |

Design decision IDs (FN-VER-*) are recorded in `00-design-decisions.md`:
- **FN-VER-1**: An edit-mode draft on a Published Function instance is marked by a small red SVG asterisk overlaid on the existing S badge, with the asterisk's visible center sitting on the badge's top-right corner. The S badge itself is unchanged (still indigo, still "Shared / Published"). The asterisk uses `#DC2626` light / `#F87171` dark, a 14×14 wrapper box centered via `transform: translate(50%, -50%)`, and a 3-layer drop-shadow halo (white in light, ink in dark) for legibility against the badge fill. SVG path is preferred over the text `*` character because text asterisks are top-heavy in their line box and cannot reliably center-align with the corner point.
- **FN-VER-2**: Hovering the asterisk opens a shadcn-style tooltip titled "Edit-mode draft" with a body that explains the source version and points the user at the kebab-Publish and kebab-Drop changes affordances. The tooltip is dark-on-light in light theme, inverted in dark. Tooltip does NOT appear on the S badge itself (which keeps its existing "Shared Function" tooltip via the L/S badge component); it appears only on the asterisk hit region.
- **FN-VER-3**: The publish modal opened from edit mode is a variant of the publish-to-library dialog. It has a locked target context chip at the top of the body (above all form fields), showing the function name and the source version (`<Function> · from edit mode · source v1.4.2`). The chip is read-only - there is no library-Function picker, because the source is always known from the edit-mode entry context. The chip uses the indigo S-badge palette so it visually echoes the badge on the originating block. There is no mode toggle (no New/Major tabs) - each entry point opens its own purpose-built dialog: a Local Function's "Publish to Library" opens the "new library entry" dialog (unchanged); an edit-mode "Publish" opens this modal.
- **FN-VER-4**: The Version field in the edit-mode publish modal is a smart dropdown (NOT a free input). The trigger shows the auto-derived bump target (next patch / minor / major depending on what the draft changed vs source) with a color-coded bump chip - green for patch, amber for minor, red for major. The trigger gains a red outline + faint red ring when the only valid target is MAJOR (signals the user that this is a breaking publish). Clicking the trigger opens a dropdown with all three bump options + a Custom section with a text input that accepts arbitrary semver including pre-release / build metadata (e.g. `1.5.0-alpha.1`).
- **FN-VER-5**: Bump options that the current draft makes invalid are visually disabled in the dropdown and carry a trailing `(i)` info icon. Hovering the `(i)` opens an inline tooltip explaining what specifically blocks that target (e.g. "PATCH cannot include input or output changes. Required input <em>tenant_id</em> was added." / "MINOR cannot add a REQUIRED input. Make <em>tenant_id</em> optional, or bump to MAJOR."). The tooltip positions below the dropdown row (not to the right) so it stays within the modal bounds. Wireframes render one tooltip statically as the demonstration; only one tooltip is ever visible at a time at runtime (the hovered one).
- **FN-VER-6**: A custom-typed version in the Version field's Custom input is validated immediately against the same rule set as the dropdown options. If the typed version implies a bump target the draft cannot support, an inline error appears under the input identifying the offending bump level and the reason in plain language (e.g. "1.4.3 is a PATCH bump - incompatible with the current draft (input was added)."). The input gains a red border + faint red ring while invalid. Publish stays disabled until either the version typed becomes valid or the user picks an enabled option from the list.
- **FN-VER-7**: Changelog is mandatory on edit-mode publish. The Changelog label carries a red `*` marker. The Publish button is disabled (visibly grayed, not just `aria-disabled`) until a non-empty Changelog entry exists. This contrasts with the publish-to-library dialog where Changelog is optional for the initial release (FN-LC-3). The reason is that every edit-mode publish creates a NEW version of an existing entry, and "what changed since the prior version" is mandatory context for library consumers.
- **FN-VER-8**: Description, Tags, and Details in the edit-mode publish modal pre-fill from the source version's metadata and remain editable. The Details field is editable specifically (here it is a full textarea so the publisher can refine long-form documentation as part of the publish). Description and Tags are per-version (each immutable version records its own copies), so editing them during publish establishes the new version's values without altering the source version's record.
- **FN-VER-9**: When a Test references a Published Function at a version that no longer exists in the library, the backend surfaces a distinct validation error code (`missing_function_version`, distinct from `missing_function_id`). Block-state propagation matches any other blocking validator: Run, Validate, and Save are all blocked at the canonical pipeline level so consumers route the error appropriately. No silent fallback to the latest version - the user must pick a valid version explicitly.
- **FN-VER-10**: The canvas-block visualization for a missing-version instance reuses the existing red-triangle validation alert (`node-validation-alert.tsx`) in the status-bar left, immediately before the S badge. Same icon, same color, same hover affordance as any other validation alert - the tooltip body identifies the specific missing version and points the user to the config modal as the recovery path ("Pins v1.4.2, not in library. Open config to pick another version."). Pulse animation may be enabled to draw the eye, matching how the existing alert handles "needs attention" severity.
- **FN-VER-11**: The non-edit-mode Published config modal opened on a missing-version instance carries (a) a destructive banner at the top of the body naming the missing version and the recovery path (just "Pick an available version from the dropdown."), (b) a red-bordered Version field trigger with a faint red ring, the version text rendered in strikethrough, and a destructive "Missing" chip next to it, and (c) a dropdown that lists ONLY the available versions (NOT the missing pinned one - it would be redundant and unpickable, and is already surfaced in the trigger + banner). The Make Local kebab entry is disabled when the source version is missing (the source definition is gone, so the detach cannot copy anything); the disabled state has a tooltip explaining why. The single recovery path is: pick an available version from the dropdown + Save.
- **FN-VER-12**: Library cards (in the Functions Library modal and the `/functions` page) carry a version pill at the bottom-right of the card, on the same row as the tags. Pill is mono-font, indigo (matches the S-badge palette: `bg-indigo-500/12 text-indigo-700 border-indigo-500/25`), 10.5px font, small padding. Layout: row 1 `f-icon + name` (name takes full row width, truncates with ellipsis), row 2 description (truncated), row 3 `[tags clipped to fit] [(+N) overflow chip] [version pill]` anchored right via flex `justify-content: space-between`. No version-count chip - keep the metadata minimal at card density; full version history is one click away in the instance config modal.
- **FN-VER-13**: Two hover-tooltip affordances on the library card. (a) The name span has `cursor: help` and, when truncated, a tooltip shows the full name on hover (single-line, anchored top-left, dark popover in light / inverted in dark). (b) The `(+N)` tag overflow chip (when present, monospace, neutral chip color so it doesn't compete with the indigo tag chips) has `cursor: help` and a tooltip listing all tags. Both follow the same shadcn-style tooltip pattern used elsewhere in WAVE.

---

Design decision IDs FN-VMGR-*, FN-BC-*, FN-PARAM-* and FN-VAR-* are registered here, in the list below; `design/03-component-design/05-function-management/07-canvas-integration.md` and `09-schema-editor.md` describe the design they govern without listing the IDs.
- **FN-VMGR-1**: Var Manager inside a local Function hosts a PARAMETERS group (above) and the existing VARIABLES group (below). Outside a Function the Var Manager renders today's layout (no PARAMETERS group).
- **FN-VMGR-2**: PARAMETERS group is split by `INPUTS` / `OUTPUTS` sub-separator headers. Both sub-sections are part of the same collapsible parent.
- **FN-VMGR-3**: IN badge (green) marks declared input parameters. OUT badge (orange) marks declared output parameters. The OUT badge is the same shape and color the Var Manager already uses for plugin-output-bound variables; the section header (`PARAMETERS → OUTPUTS` vs `VARIABLES`) disambiguates the two meanings.
- **FN-VMGR-4**: "+ Add" becomes "+ Add ▾" when inside a Function. The dropdown is Input parameter (→ glyph) / Output parameter (← glyph) / divider / Variable (x glyph). Outside a Function the button reverts to the single-action "+ Add" form.
- **FN-VMGR-5**: Inside a Function the Variable Manager hides all external scopes (system / regression / suite / test); only PARAMETERS and VARIABLES are visible. Expression autocomplete is gated the same way.
- **FN-BC-1**: A `function` BreadcrumbSegmentType is added. Function segments render in violet (`#a78bfa` muted, `#c4b5fd` leaf) with the `ƒ` icon (lucide `FunctionSquare`). The styling differentiates drill segments from entity-list segments (suite / regression / test).
- **FN-BC-2**: The breadcrumb path is `<nav-origin segments> / <Test name> / <Function 1 name> / ... / <Function N name>`. When drill state is empty the breadcrumb carries no Function segments.
- **FN-BC-3**: Clicking a parent Function segment pops the drill stack to that depth. Clicking the parent Test segment pops the entire drill stack (returns to the Test canvas). Clicking the leaf is a no-op.
- **FN-BC-4**: When drilled in, the back arrow pops one drill level (= equivalent to clicking the segment immediately to the left of the leaf). When not drilled, the back arrow keeps its usual behavior (navigates to the originating page).
- **FN-PARAM-1**: Parameter creation reuses the existing Create Variable component (same source files; no separate parameter-editor component). A `mode` prop ('variable' | 'input' | 'output') drives per-mode customizations. There is no parallel codebase to maintain.
- **FN-PARAM-2**: Modal title varies by mode: "Create Input Parameter" / "Create Output Parameter" / "Create Variable". Subtitle gives a one-liner role explanation. The `Default Value` field carries a mode-specific helper: `(used when Required is off and caller omits)` for inputs, `(= fallback if not written)` for outputs, no helper for vars. Superseded by VMGR-97 to VMGR-100 and VMGR-106 (titles "New ..." / "Edit ...").
- **FN-PARAM-3**: A Required flag is rendered in Input mode only. When checked: the Function Block must set a value; Test execution blocks if no value is set, and a default, if any, applies only when the Function runs on its own (VMGR-113). When unchecked (default): the Function Block may leave it unset; the default applies. Output mode and Variable mode never render the Required flag.
- **FN-PARAM-4**: Duplicate-name validation: inputs, outputs, and locals share a single per-Function namespace, so duplicate names are rejected regardless of category (two Inputs named `x`, two Outputs named `x`, an Input + Output sharing a name, or an Input + local sharing a name all surface as inline errors with Save disabled).
- **FN-PARAM-5**: Enum mechanism is bound to the Array type. A "Create enum" flag is rendered only when Type=Array. When checked: a Value Type dropdown appears as a new row directly below Type (allowed values: String, Integer, Float - other types are not enum-able); the existing Default Value array editor holds the allowed-values literal (no separate "Allowed values" UI); the `{x}` expression-mode toggle on Default Value is disabled (literals only); in Input mode the Required flag is forced-checked and locked while Create enum is on; Save validates every value in the Default Value array against the chosen Value Type. Unchecking Create enum releases the Required lock and re-enables expression mode. Superseded by VMGR-97 to VMGR-100 and VMGR-112.
- **FN-PARAM-6**: All flag checkboxes (Required, Create enum, Mark as secret) share one visual style - identical-sized rows with a checkbox + "Name (helper text in parens)" - stacked together below the Default Value field. No grouping box, no section header, no per-flag highlighting. The locked Required is drawn with a grayed-out checkbox and an italicized "(locked while Create enum is on)" inline note; the row still matches the others in size and structure. Superseded by VMGR-97 to VMGR-100.
- **FN-VAR-1**: Inside a Function, variables are referenced by bare name (no `input.` or `output.` prefix). The IN / OUT row badges in the Variable Manager and the matching badges in expression autocomplete identify each name's role; the runtime resolves direction via the declared schema. This aligns Function variable usage with how local variables work today at the Test level - one name, no prefix.

---

### function-view/ (light + dark pairs)

Wireframes for the standalone Function View canvas - the read-only / run / edit / publish surface opened from the `/functions/{id}` detail page with no parent Test.

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `e2-edit-chrome-publish-light.png` | VIEW-6 | Drilled-in edit-mode action-bar chrome with the new Publish button: `Select Environment` / amber `EDIT MODE` pill / amber-outline `Drop changes` / primary-blue `Publish` (Upload icon, rightmost in the edit cluster, before the splitter) / `Debug` / blue `Run`. Light theme. |
| `e2-edit-chrome-publish-dark.png` | VIEW-6 | Same, dark theme. |
| `e2-publish-confirm-light.png` | VIEW-7 | Single-outcome publish confirm for the library View: Upload icon in an indigo square, title "Publish a new version?", mono `<name> · vSrc -> vTgt` line (target in accent), body "...The View switches to the new version.", footer Cancel + primary Publish. AlertDialog semantics (no ESC/backdrop dismiss). Light theme. |
| `e2-publish-confirm-dark.png` | VIEW-7 | Same, dark theme. |
| `e2-breadcrumb-light.png` | VIEW-2 | Library-View breadcrumb: back arrow + `[f]` box + Function name ONLY (no Test segment), Reset + Idle status on the right. The back arrow returns to `/functions/{id}`. Light theme. |
| `e2-breadcrumb-dark.png` | VIEW-2 | Same, dark theme. |
| `e2-palette-icon-light.png` | VIEW-8 | Workbench palette "Function Lib" button with the FunctionSquare glyph (replacing the legacy Blocks glyph). Light theme. |
| `e2-palette-icon-dark.png` | VIEW-8 | Same, dark theme. |

Design decision IDs (VIEW-*) are recorded in `00-design-decisions.md` § 4.11 Function View Canvas.

---

### reports/

**Canonical wireframes for generated execution reports are the exact approved HTML documents** (interactive: theme switch, log level filter, column selector, collapsible chart, hover tooltips). The PNGs are area-of-interest captures of those HTMLs for quick visual reference - NOT the canonical artifact.

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `suite-exec-report.html` | REPORT-1 through REPORT-14 | Canonical Suite execution report document (4 tests, 2 failed; expanded chart) |
| `test-exec-report.html` | REPORT-1 through REPORT-13 | Canonical Test execution report document (per-block timeline, nested paths, empty errors state) |
| `regression-exec-report.html` | REPORT-1 through REPORT-14 | Canonical Regression execution report document (2 suites, per-suite table headers and chart sub-sections) |
| `suite-exec-report-header-{light,dark}.png` | REPORT-2, REPORT-3, REPORT-4 | Brand row, status, theme switch, title with suite icon + chip, 3x2 meta grid |
| `suite-exec-report-results-{light,dark}.png` | REPORT-5 | Test count cards |
| `suite-exec-report-timeline-{light,dark}.png` | REPORT-6, REPORT-7 | Timeline table + collapsible full-width chart with order-number labels |
| `suite-exec-report-errors-{light,dark}.png` | REPORT-11 | ERROR and FATAL error cards |
| `suite-exec-report-logs-{light,dark}.png` | REPORT-12, REPORT-13, REPORT-14 | Logs table with headers, level filter, column selector |
| `test-exec-report-header-{light,dark}.png` | REPORT-2, REPORT-3, REPORT-4 | Test icon + chip variant |
| `test-exec-report-results-{light,dark}.png` | REPORT-5 | Block count cards |
| `test-exec-report-timeline-{light,dark}.png` | REPORT-7, REPORT-9, REPORT-10 | Per-block timeline with nested "Parent / Child" paths |
| `test-exec-report-errors-{light,dark}.png` | REPORT-11 | Empty errors state |
| `regression-exec-report-header-{light,dark}.png` | REPORT-2, REPORT-3, REPORT-4 | Regression icon + chip variant |
| `regression-exec-report-timeline-{light,dark}.png` | REPORT-6, REPORT-8 | Suite-grouped table with repeated headers; per-suite chart sub-sections |

Design decision IDs (REPORT-*) are recorded in `00-design-decisions.md` § 4.12 Execution Reports (Generated Documents).

---

### report-viewer/

**Canonical wireframes for the in-app Report Viewer are the approved HTML documents.** The PNGs are area-of-interest captures of those HTMLs for quick visual reference - NOT the canonical artifact.

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `report-viewer-suite.html` | RVIEW-1 through RVIEW-9 | Canonical viewer page for a suite execution (runs gantt, 2 errors, filtered logs) |
| `report-viewer-test.html` | RVIEW-1 through RVIEW-9 | Canonical viewer page for a test execution (blocks gantt with nested paths, errors empty state) |
| `report-generating.html` | RVIEW-10 | Canonical generation interstitials (generating / failed / still-running states) |
| `reports-list.html` | RVIEW-11, RVIEW-12 | Canonical /reports list page (Report column, View vs Generate actions) |
| `report-entry-points.html` | RVIEW-13 | Canonical entry-point button placements (exec-detail toolbar, history action bar) |
| `report-viewer-suite-header-{light,dark}.png` | RVIEW-4 | Viewer detail header: back, icon, name, SUITE chip, status, Download JSON + Export HTML |
| `report-viewer-suite-summary-{light,dark}.png` | RVIEW-5 | Summary card: generated-at aside, 3x2 meta grid, test count cards |
| `report-viewer-suite-timeline-{light,dark}.png` | RVIEW-6, RVIEW-7 | Runs gantt with time axis, linked run names, status bars, durations |
| `report-viewer-suite-errors-{light,dark}.png` | RVIEW-8 | ERROR and FATAL cards with paths and timestamps |
| `report-viewer-suite-logs-{light,dark}.png` | RVIEW-9 | Logs card with Level dropdown and "N of M entries" count |
| `report-viewer-test-summary-{light,dark}.png` | RVIEW-5 | Block count cards variant (Blocks / ... / Not Run) |
| `report-viewer-test-timeline-{light,dark}.png` | RVIEW-6 | Blocks gantt with muted "Parent /" nested path prefixes |
| `report-viewer-test-errors-empty-{light,dark}.png` | RVIEW-8 | Success-tinted "No errors recorded" empty state |
| `report-generating-progress-{light,dark}.png` | RVIEW-10 | Generating card: spinner, progress bar, "3 of 7 runs processed" |
| `report-generating-failed-{light,dark}.png` | RVIEW-10 | Failed card: message, Try Again, View Execution |
| `report-generating-running-{light,dark}.png` | RVIEW-10 | 409 still-running card: message, View Execution, Back to Reports |
| `reports-list-page-{light,dark}.png` | RVIEW-11, RVIEW-12 | Full list page: filters, table with Report column, pagination |
| `report-entry-exec-toolbar-{light,dark}.png` | RVIEW-13 | Report button between Re-run and Export on the execution detail header |
| `report-entry-history-bar-{light,dark}.png` | RVIEW-13 | Report button before Open in Workbench on the historical canvas action bar |

Design decision IDs (RVIEW-*) are recorded in `00-design-decisions.md` § 4.13 Report Viewer (In-App).

---

### artifacts/

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `artifact-browser-list-{light,dark}.png` | ARTIF-1, ARTIF-2 | Execution-centric Artifacts list: Execution / Type / Status / Finished / Artifacts / Size columns, selection mode, Mass action menu (Download .zip + Delete artifacts), per-row chevron + kebab |
| `artifact-browser-drill-{light,dark}.png` | ARTIF-3 through ARTIF-12 | Execution artifact drill: detail header + Download all, Show removed toggle, Failure summary / Reports / Logs (Tree) / Files (Flat) collapsible sections, entity-iconed Logs tree with status-tinted test leaves, per-file and per-node size + download + delete, name truncation popover, muted removed (tombstone) rows |
| `session-artifacts-chip-{light,dark}.png` | ARTIF-14 | Workbench canvas breadcrumb bar with the "Artifacts" chip (count badge) on the right side, left of Reset, sharing Reset's history-mode gating |
| `session-artifacts-sheet-{light,dark}.png` | ARTIF-15, ARTIF-16 | Floating Session Artifacts sheet (DraggableSheet family): header with count + total size + refresh + close, drill-idiom file rows (type tile, mono name, folder subtitle, size, download + delete), ephemerality footer note; empty state variant |
| `session-artifacts-wipe-dialogs-{light,dark}.png` | ARTIF-17 | Warn-on-wipe dialogs: NEW destructive Reset Session confirm, and the shared amber artifact-loss callout added to the existing Close / Switch dialogs |

Design decision IDs (ARTIF-*) are recorded in `00-design-decisions.md` § 4.14 Artifact Browser.

---

### testdata/

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `td-chip-{light,dark}.png` | TDATA-3 | Canvas breadcrumb right cluster with the Test Data chip left of the Artifacts chip, then Reset and the status pill |
| `td-sheet-{light,dark}.png` | TDATA-4, TDATA-5, TDATA-6, TDATA-7 | Floating Test Data sheet: header (folder icon, title, Upload and New folder text buttons, Refresh and Close icon buttons), filter row with "N files - size", tree with an expanded folder, file rows with Copy path + Download + kebab, footer note |
| `td-sheet-empty-{light,dark}.png` | TDATA-6 | The sheet's empty state with the Upload files button |
| `td-picker-file-{light,dark}.png` | TDATA-8, TDATA-9 | "Choose a file" picker: Test Data / Artifacts tabs, filter + Upload, tree with a selected file, Reference line, Cancel / Select |
| `td-picker-folder-{light,dark}.png` | TDATA-8, TDATA-9 | "Choose a file or folder" picker with a folder selected: Reference `testdata://fixtures`, primary reads Select |
| `td-picker-dir-{light,dark}.png` | TDATA-8, TDATA-9 | "Choose a folder" picker: files muted, a folder selected, Select |
| `td-picker-save-{light,dark}.png` | TDATA-8, TDATA-9 | "Save as" picker: Artifacts only under the hint, Name field under the tree, Reference composed from folder + name, Cancel / Select |
| `td-copy-path-{light,dark}.png` | TDATA-7 | Artifacts drill Files rows with Copy path before Download and Delete |
| `td-row-actions-{light,dark}.png` | TDATA-5, TDATA-7 | Test Data rows: file kebab open (Rename, Delete), a folder row, and a file row in the copied (check) state |

Design decision IDs (TDATA-*) are recorded in `00-design-decisions.md` § Test Data and File References.

---

### export/ (light + dark pairs)

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `export-dialog-secrets-default-{light,dark}.png` | EXPORT-1, EXPORT-3, EXPORT-6 | Shared export dialog with the "Secret values" radio group (Mask default / Keep encrypted / Decrypt) and one-line muted descriptions; Format group unchanged above |
| `export-dialog-secrets-decrypt-{light,dark}.png` | EXPORT-2 | Same dialog with Decrypt selected: amber inline warning ("Secrets will be written in plain text. Handle the exported file securely.") between the radio group and the footer |
| `backup-secrets-mode-{light,dark}.png` | EXPORT-4 | Create Backup section with the Secret values radio placed after the Compression Level slider (replaces the Include-credentials toggle + red warning); Decrypt selected showing the amber warning; Periodic Backup carries the identical control. |
| `import-foreign-secret-warning-{light,dark}.png` | EXPORT-5 | Shared import review step with a per-entity amber sublabel on rows whose secrets were encrypted by another WAVE instance; on import each such value is stored as null and the secret is owed until a person enters it |

Design decision IDs (EXPORT-*) are recorded in `00-design-decisions.md` § 4.15 Export Secrets Handling.

---

### secrets/ (light + dark pairs)

| File | Design Decision IDs | Description |
|------|---------------------|-------------|
| `secret-var-authoring-columns-{light,dark}.png` | SECUI-1 through SECUI-9 | Secret Variable authoring: the shared masked value cell + Secret column across every variable-authoring surface (variable manager, setter rows, output bindings, suite / regression / system grids, profile parameters); write-only replace + un-secure confirm-and-clear |
| `secret-masking-fields-{light,dark}.png` | SECMASK-1 through SECMASK-4 | Per-block Secret masking control: a collapsible section placed last in Input Parameters (peer to the plugin's other parameter-group collapsibles), listing the fields the plugin declares as credential-bearing (HTTP: its eight known sensitive headers) as a check / uncheck list, masked by default; unchecking reveals a field's value for that block |
| `secret-reveal-block-{light,dark}.png` | SECREV-1 through SECREV-3 | Block "Secrets" collapsible (the SECMASK section renamed "Secrets", now on every plugin): the "Masking in run logs & reports" tri-state selector (Use system setting / Always reveal / Always mask), its contextual helper / amber warning, the collapsed-row "Revealing" pill, and the "Mask specific fields" list which grays out when run output is revealed |
| `secret-reveal-badge-{light,dark}.png` | SECREV-4 | Canvas "unsecured" amber triangle in the block's validation-badge slot: mutually exclusive with the red misconfiguration triangle (red wins), shown when the block's effective run-output state is revealing and it has no config errors; hover tooltip |
| `secret-reveal-settings-{light,dark}.png` | SECREV-6, SECREV-7 | Settings > General "Secret Masking" section: three reveal-toggles (Run output / Variable inspection & watchers / Variable Manager), all off by default = masked, amber "Revealing" cue on an on-toggle, and the exports / encryption-at-rest carve-out footnote. Superseded by `utility/settings-general-{light,dark}.png`, which shows the page as it is: four reveal switches, Cancel and Save on the Logging heading line |
| `credential-field-states-{light,dark}.png` | SECFLD-1 through SECFLD-4 | Declared credential input fields (SSH Session Open password / private key / passphrase): the four value states - literal before save (lock icon + protected tooltip), saved write-only masked literal, expression on a non-secret variable (amber alert + tooltip), expression on a secret variable (lock) - with the status icon in one slot at the right inside the value field |

Design decision IDs (SECUI-*, SECMASK-*, SECREV-*, SECFLD-*) are recorded in `00-design-decisions.md` § 4.19 Secret Variable Authoring UI, § 4.20 Per-Block Secret Masking Control, § 4.21 Controlled Secret Reveal, and § 4.22 Declared Credential Fields.

---

## Component Source of Truth

**IMPORTANT**: Reusable components appear in multiple wireframes. Some wireframes show older versions of these components. The following table identifies the **authoritative wireframe** for each component. When implementing, always reference these source-of-truth frames.

### Why This Matters

Wireframes were created iteratively. Later refinements to components (like the palette) weren't backported to earlier wireframes to avoid wasted effort. This follows DRY principles - the component design lives in ONE place.

### Authoritative Component References

| Component | Source of Truth Wireframe | Design Decisions | Notes |
|-----------|---------------------------|------------------|-------|
| **Expanded Sidebar** | `navigation/sidebar-expanded.png` | SHELL-1 to SHELL-6 | Nav structure, icon colors, section headers |
| **Collapsed Sidebar** | `navigation/sidebar-collapsed.png` | SHELL-1 to SHELL-6 | 56px width, icon-only mode |
| **Palette - Controls** | `tools-palette/palette-controls-section.png` | CANVAS-97 to CANVAS-104 | All controls with icons |
| **Palette - Plugins** | `tools-palette/palette-plugins-section.png` | CANVAS-105 to CANVAS-111 | All plugins; the frame's "Orchestration" category is "Kubernetes" in the product - see Known Discrepancies below |
| **Collapsed Palette** | `tools-palette/palette-collapsed.png` | CANVAS-13 to CANVAS-18 | Icon strip with colored icons |
| **Palette - Recents** | `tools-palette/palette-recents.png` | CANVAS-9 to CANVAS-12 | Flyout with 8 recent items |
| **Palette - Most Used** | `tools-palette/palette-most-used.png` | CANVAS-9 to CANVAS-12 | Flyout with 8 frequent items |
| **Variable Manager** | `workbench/vmgr-panel.png` | VMGR-1 to VMGR-14 | Flat row list, filter + sort toolbar, four-icon action cluster |
| **Console Panel** | `workbench/workbench-console-expanded.png` | CANVAS-4 to CANVAS-8 | 200px height, tabs, Clear Output |
| **Breadcrumb Row** | `workbench/workbench-breadcrumbs-bar.png` | CANVAS-68, CANVAS-69 | Reset link, status indicator |
| **Element Config Modal** | `modals-elements/element-configuration-modal.png` | CANVAS-124 to CANVAS-151 | Version, INPUT/OUTPUT, Profiles button |
| **Table Pattern** | `lists-build/tests-list-populated.png` | LIST-1 to LIST-9 | Columns, pagination, filters |
| **Loading State** | `lists-build/list-loading.png` | LIST-4 | Skeleton rows pattern |
| **Empty State** | `lists-build/tests-list-empty.png` | LIST-6 | Icon, message, CTA |
| **Error State** | `lists-build/list-error.png` | LIST-5 | Alert icon, Try Again |
| **Blocked State** | `lists-build/list-blocked.png` | LIST-10 to LIST-17 | Blurred inert content, card, Try Again, folded Details |
| **Run Dialog** | `workbench/workbench-run-dialog.png` | RUN-1 to RUN-15 | Environment selector, split button |
| **Delete Confirmation** | `modals-build/suite-delete.png` | FORM-20 to FORM-30 | Simple and Enhanced patterns |

### Known Discrepancies (Do Not Fix)

The following wireframes show **older versions** of components. They remain as-is because:
1. The effort to update them doesn't add implementation value
2. The design decisions document is the implementation spec
3. Implementers should reference the source-of-truth frames above

| Wireframe | Outdated Component | Correct Reference |
|-----------|-------------------|-------------------|
| `canvas/canvas-populated.png` | Palette (6 controls, no icons) | `tools-palette/palette-controls-section.png` |
| `workbench/workbench-console-expanded.png` | Palette (6 controls, no icons) | `tools-palette/palette-controls-section.png` |
| `historical/workbench/workbench-vars-manager-expanded.png` | Palette (6 controls, no icons) | `tools-palette/palette-controls-section.png` |
| `canvas/canvas-empty.png` | Palette (6 controls, no icons) | `tools-palette/palette-controls-section.png` |
| `canvas/canvas-debug-paused.png` | Palette (6 controls, grayed) | `tools-palette/palette-controls-section.png` |
| `tools-palette/palette-collapsed.png` | Flyout (6 controls) | `tools-palette/palette-controls-section.png` |
| `tools-palette/palette-plugins-section.png` (and canvas frames) | "Orchestration" category label | "Kubernetes" - the current palette category name |

### Future Wireframe Guidelines

For any future wireframes:
1. **Use placeholders** for reusable components (gray box with label, or skeleton pattern)
2. **Reference existing frames** rather than duplicating component details
3. **Only create detailed component frames** when introducing NEW components

---

## Component Consistency Checklist

### Sidebar Navigation (All Pages)

Every wireframe showing a page (not a modal) MUST have consistent sidebar per SHELL-1 through SHELL-6:

| Requirement | Decision ID | Check |
|-------------|-------------|-------|
| Nav icons color-coded by section | SHELL-1 | Dashboard=#F472B6, Executions=#60A5FA, Tests=#4ADE80, Workbench=#FBBF24, Blocks=#F87171, Plugins=#A78BFA, Profiles=#38BDF8, Artifacts=#FB923C, Regressions/Suites/Reports=#A1A1AA, Settings/User=$olive11 |
| Selected nav: white icon on $blue10 background (40x32px, 6px radius) | SHELL-2 | Verify selected item matches this pattern |
| Bottom row: theme toggle (left), collapse button (right), divider above | SHELL-3 | All pages must show this |
| ACCOUNT section (Settings, User) in nav list | SHELL-4 | Consistent with other nav items |
| Collapsed sidebar: 56px width, icons only | SHELL-6 | Canvas/Workbench wireframes show collapsed sidebar |

**Pages to verify (35 unique page wireframes)**:
- [ ] dashboard/dashboard-populated.png, dashboard/dashboard-empty.png
- [ ] lists-build/tests-list-*.png (5 variants)
- [ ] lists-build/suites-list-*.png (2 variants)
- [ ] lists-build/regressions-list-*.png (2 variants)
- [ ] lists-build/executions-list-*.png (2 variants)
- [ ] lists-build/list-loading.png, lists-build/list-error.png, lists-build/list-blocked.png (generic states)
- [ ] canvas/canvas-*.png (5 variants)
- [ ] details/suite-detail.png
- [ ] details/regression-detail.png
- [ ] details/suite-execution-detail.png
- [ ] details/regression-execution-detail.png
- [ ] lists-library/profiles-list-populated.png
- [ ] lists-library/blocks-list-populated.png
- [ ] lists-library/plugins-list-populated.png
- [ ] utility/settings-page.png

---

### Modal Patterns

All modals MUST follow these patterns:

| Requirement | Decision ID | Applies To |
|-------------|-------------|------------|
| Entity forms: 400px width, centered | FORM-5, FORM-31 | suite-create-edit, regression-create-edit, profile create/edit |
| Header: drag handle + title + close button | CANVAS-148, PROFILE-13 | Element Config Modal, Profiles Sub-Modal, Blocks Library |
| Footer: destructive action (red) left, Cancel + Primary right | FORM-13 | All edit modals with delete option |
| Semi-transparent overlay (#00000080) | FORM-4 | All modals over page content |
| Active trigger highlighted ($blue10) | CANVAS-150 | Gear button when Element Config Modal open |

---

### Button Patterns

| Pattern | Decision ID | Usage |
|---------|-------------|-------|
| Primary action: $blue10 background | Multiple | Create, Save, Run, Add |
| Destructive action: #dc2626 (red) background | FORM-26 | Delete buttons in confirmation dialogs |
| Destructive text: red text, no background | FORM-13 | "Delete Suite" in edit modal footer |
| Split button: [Action \| ▾] | RUN-5, RUN-6 | Run and Debug buttons in Canvas/Workbench |
| Disabled: $mauve8 | BULK-4 | Mass Action dropdown when 0 selected |

---

### Table Patterns

| Requirement | Decision ID | Applies To |
|-------------|-------------|------------|
| Name column (left) and Actions column (right) sticky | LIST-1 | All entity lists |
| Full pagination: count, page size, navigation | LIST-2 | All lists with pagination |
| Single-page pagination disabled ($mauve8) | LIST-3 | Right-side controls when 1 page |
| Loading: 9 skeleton rows, varying bar widths | LIST-4 | All list loading states |
| Error: empathetic tone, "Try Again", red alert | LIST-5 | All list error states |
| Empty: entity icon, encouraging message, CTA | LIST-6 | All list empty states |
| Blocked: warning icon, "Try Again", folded Details, sidebar untouched | LIST-10 through LIST-17 | All list blocked states |

---

## Known Integration Points

These decisions reference integration with other wireframes:

| Decision | Integration | Verification Needed |
|----------|-------------|---------------------|
| PROFILE-11 | "Profiles" button in Element Config Modal footer | Verify modals-elements/element-configuration-modal.png includes this |
| CANVAS-150 | Gear button highlighted when modal open | Verify canvas/canvas-element-selected.png shows blue gear |
| RUN-1 | Environment selector in Canvas header | Verify workbench/workbench-run-dialog.png shows header selector |
| LISTRUN-1 | Run modal appears over list | Verify modals-build/regression-run.png shows modal over list |

## Design Decision ID Ranges

Quick reference for decision ID allocation. All IDs are defined in `00-design-decisions.md`,
as table rows whose first cell is the bare ID.

The table is keyed on prefix, not section: one prefix spans several sections (CANVAS spans 18,
VMGR spans 6) and one section can carry several prefixes (Element Configuration Modal holds
CANVAS, FN-LC and FN-VER). `Highest` is the watermark an author needs when allocating the next
ID. `Defined` is how many IDs actually exist, and it is the column the total sums. Where the two
differ, `Gaps` lists the numbers inside the range that were never defined - those IDs are not
citable.

| Prefix | Area | Highest | Defined | Gaps |
|--------|------|---------|---------|------|
| ARTIF | Artifact Browser | 17 | 17 | - |
| BACKUP | Settings Backup & Restore | 9 | 9 | - |
| BLOCK | Blocks List | 10 | 10 | - |
| BULK | Entity Lists - bulk selection | 4 | 4 | - |
| CANVAS | Test Canvas | 247 | 189 | 19-28, 152-199 |
| CSV | CSV Parser Config | 12 | 12 | - |
| DASH | Dashboard | 23 | 23 | - |
| DEBUG | Debug Options Popover | 8 | 8 | - |
| ENV | Environment Selector Popup | 16 | 16 | - |
| EXEC | Suite Execution | 26 | 26 | - |
| EXPORT | Export Secrets Handling | 7 | 7 | - |
| FIO | File I/O Block | 11 | 11 | - |
| FN-LC | Function Lifecycle | 17 | 17 | - |
| FN-VER | Function Versioning | 13 | 13 | - |
| FNCFG | Function Config Modal | 9 | 9 | - |
| FNDETAIL | Function Detail | 14 | 14 | - |
| FNLIST | Functions List | 12 | 12 | - |
| FOCUS | Focus Current (canvas navigation) | 2 | 2 | - |
| FORM | Forms (create / edit / delete) | 38 | 38 | - |
| GEN | General | 5 | 5 | - |
| HELM | Helm Blocks | 12 | 12 | - |
| HTTP | HTTP Plugin Rework | 16 | 16 | - |
| K8SCON | K8s Connect Config | 7 | 7 | - |
| K8SEXEC | K8s Exec Channel Blocks | 10 | 10 | - |
| K8SPROF | Kubernetes Profile | 9 | 9 | - |
| K8SREAD | K8s Read Blocks | 20 | 20 | - |
| K8SWRITE | K8s Write Blocks | 8 | 8 | - |
| LIST | Entity Lists | 26 | 26 | - |
| LISTRUN | List View Run Modal | 12 | 12 | - |
| MCP | MCP Server Settings | 9 | 9 | - |
| NET | Settings Network Group | 11 | 11 | - |
| NETCAT | Netcat Block | 19 | 19 | - |
| OS | OpenSearch Block | 16 | 16 | - |
| PARALLEL | Parallel Control | 8 | 8 | - |
| PICKER | Entity Picker Modal | 5 | 5 | - |
| PING | Ping Block | 18 | 18 | - |
| SQL | SQL Block | 15 | 15 | - |
| SFTP | SFTP Block | 10 | 10 | - |
| FIELD | One Value Field | 13 | 13 | - |
| FIELDERR | Field-Level Save Errors | 3 | 3 | - |
| PLUGIN | Plugins List | 11 | 11 | - |
| PROFILE | Profiles | 54 | 54 | - |
| REG | Regression Detail | 22 | 22 | - |
| REG-EX | Regression Execution | 25 | 25 | - |
| REMEX | Remote Execution (container) | 6 | 6 | - |
| REMICON | Remote Execution plugin icons | 1 | 1 | - |
| REPORT | Execution Reports (generated documents) | 15 | 15 | - |
| RUN | Run Dialog (canvas / workbench) | 15 | 15 | - |
| RUNM | Live-Execution Mirroring | 10 | 10 | - |
| RVIEW | Report Viewer (in-app) | 13 | 13 | - |
| SAVE | Floating editors under a surface Save | 1 | 1 | - |
| SECFLD | Declared Credential Fields | 4 | 4 | - |
| SECMASK | Per-Block Secret Masking | 4 | 4 | - |
| SECREV | Controlled Secret Reveal | 7 | 7 | - |
| SECUI | Secret Variable Authoring UI | 13 | 13 | - |
| SESS | Session Ownership & Continuity | 12 | 12 | - |
| SETTINGS | Settings Page | 22 | 22 | - |
| SHELL | Application Shell | 10 | 14 | - |
| SHRUN | Shell Script and Shell Exec Blocks | 19 | 19 | - |
| PYRUN | Python Block | 21 | 21 | - |
| SSH | SSH Session Plugins | 12 | 12 | - |
| SSHTUN | SSH Tunnel Plugins | 8 | 8 | - |
| SUITE | Suite Detail | 25 | 25 | - |
| SWITCH | Switch/Case Control | 13 | 13 | - |
| TDATA | Test Data and File References | 19 | 19 | - |
| VARPICK | Variable Picker | 2 | 2 | - |
| VIEW | Function View Canvas | 10 | 10 | - |
| VMGR | Variable Manager | 114 | 97 | 49-60, 76-80 |
| WAIT | Wait Until Control | 9 | 9 | - |
| WATCH | Watch-Mode Build-Up | 7 | 7 | - |
| WORKBENCH | Workbench | 14 | 14 | - |
| WSRV | WAVE Server & Browser Sessions | 11 | 11 | - |
| XLS | Excel Config | 15 | 15 | - |
| **TOTAL** | **73 prefix families** | | **1220** | |

Two shapes in `00-design-decisions.md` make the counts read oddly at a glance:

- `CANVAS-52-58` and `CANVAS-60-66` are single rows that each define seven IDs, so 1208 rows
  define 1220 IDs.
- SHELL carries lettered sub-IDs (`SHELL-7a` through `SHELL-7d`) alongside `SHELL-7`, which is
  why its `Defined` (14) exceeds its `Highest` (10).

---

## Implementation Notes

When implementing a screen:

1. **Reference this inventory** to find the correct wireframe for each screen
2. **Check design decision IDs** in `00-design-decisions.md` for detailed rationale
3. **Verify consistency** using the checklists above before marking implementation complete
4. **Write Playwright tests** that reference decision IDs (e.g., `// Per LIST-2: full pagination`)

---
