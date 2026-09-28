# Docs refresh — TASKS

## What changed since this was first written

Reading the app's own `docs/*.md` (dev specs, at
`/Users/uos/Projects/SmartCsv/smartcsv/docs/`) turned up more than a visual
refresh: the interaction model changed.

- The **five column dialogs** the public docs describe (resize, freeze,
  align, column-to-image, show/hide columns —
  `column_resize_dialog.dart`, `freeze_column_dialog.dart`,
  `column_align_dialog.dart`, `column_to_image_dialog.dart`,
  `csv_columns_selection_dialog.dart`) belong to the **old grid**, which is
  dying (`viewer-layout-panel.md`). The current grid replaces all five with
  one **Layout panel**: tap a column header, then Width / Align / Sort /
  Freeze / Type / Hide live in a panel over the grid.
- **Show as image** is gone as a standalone action; it is now a column
  **Type** (`column-types.md`) alongside Text/Number/Checkbox/Select/
  Date/Link/Image — an entirely undocumented feature.
- **Filter** is a panel over the grid with **Filter** and **Sort** tabs
  (`filter-sheet.md`, `sorting.md`), not a full-screen editor. SQL lives
  inside it as **Edit as SQL**, not a separate screen/tab.
- **Copy** is one tap in the bottom dock (no column-picker dialog). Cut,
  Clear content, and per-cell **Filter by this value** are on a long-press
  menu (`cell-content.md`).
- **Jump to row** and **select a range** still exist as dialogs, but moved
  from bottom-bar buttons into the viewer's `⋮` menu
  (`csv_viewer_more_actions.dart`).
- **Sort**, **Undo/redo**, and the **selection summary** (count/sum/avg
  over a selection) are real, current features with no page in the public
  docs at all.
- The **AI assistant** is a sheet reached from the dock, not a separate
  screen (`assistant-sheet.md`).

None of this is in the current `docs/*.md` (this repo). The plan below
updates the wording to match, and replaces the old GIFs with static PNGs
from `flutter test --update-goldens` where a golden is feasible in this
session; where writing a new golden is high-risk/low-context (a screen
needs a live view model, a loaded file, or unfamiliar provider wiring), the
task says so and text-only gets fixed instead, logged as follow-up.

Two repos:
- **App repo** (`smartcsv`): add/extend `test/design/*_test.dart`,
  regenerate `test/design/goldens/*.png`. Commit there per task.
- **Docs repo** (this one): copy PNGs into `docs/assets/images/`, update
  markdown. Commit here per task.

Golden surface: phone, 390×844 @1x (`design_test_host.dart`), matching the
existing goldens — not a device-frame screenshot like the old GIFs.

## Reusable existing goldens

`home_recent_*`, `viewer_app_bar*`, `viewer_search_bar*`, `viewer_dock`,
`viewer_how_to_use`, `viewer_status_title`, `tutorial_*`,
`chart_action_bar_*`, `chart_glyphs_*`, `editor_work_bar`,
`editor_column_rows`. Confirmed current: `flutter test test/design/` passes
(79 passed, 2 skipped) as of this plan.

Known blocker: `home_settings_*` golden is `skip: true` (live `google_fonts`
network fetch for the language dropdown — `home_shell_test.dart:273`).

## Tasks

- [x] 1. (docs) Write TASKS.md.
- [x] 2. (app) Confirm existing goldens still pass — done, no new commit
      needed.
- [ ] 3. (docs) `basics.md` — rewrite open-file text if needed, swap in
      `home_recent_light.png`.
- [ ] 4. (docs) `basics.md` — rewrite search section (already accurate per
      `searching.md`), swap in `viewer_search_bar.png`.
- [ ] 5. (docs) `basics.md` — rewrite resize/jump/select-range/copy
      sections to match the current UI (Layout panel width slider; `⋮` menu
      for jump/select-range; one-tap copy + long-press cut/clear). Reuse
      `viewer_dock.png` for the dock row.
- [ ] 6. (app) New golden: the viewer's `⋮` popup menu
      (`csv_viewer_more_actions.dart`) — self-contained, cheap to pump.
- [ ] 7. (docs) `basics.md` — use the `⋮` menu screenshot; add a short Sort
      and Undo/redo mention (both real, undocumented features).
- [ ] 8. (app) New golden: recent-file three-dot menu (share/rename/remove).
- [ ] 9. (docs) `basics.md` — share/rename/remove screenshot.
- [ ] 10. (docs) `filter.md` — rewrite for the Filter/Sort panel
      (`filter-sheet.md`); drop the "full screen" description.
- [ ] 11. (app) Add `matchesGoldenFile` capture to the existing
      `filter_sql_page_chrome_test.dart` pump (it already builds the real
      page; just missing the golden call) for the SQL editor.
- [ ] 12. (docs) `sql-query.md` — rewrite: SQL lives inside the filter panel
      via **Edit as SQL**, not its own screen; swap screenshot from task 11.
- [ ] 13. (docs) `ai-assistant.md` — rewrite per `assistant-sheet.md` (a
      dock sheet, not a chat screen); text-only unless a cheap golden turns
      up while reading the assistant sheet's widget.
- [ ] 14. (docs) `show-hide-freeze.md` — rewrite as the Layout panel's Hide
      button and Freeze stepper; note the old dialogs are legacy.
- [ ] 15. (docs) `column-to-image.md` — rewrite as the Image column **Type**
      (`column-types.md`), reachable via Layout → Type.
- [ ] 16. (docs) `align-column.md` — rewrite as the Layout panel's Align
      control.
- [ ] 17. (docs) Follow-up (not this session): a real Layout-panel golden
      (column scope + grid scope) to replace the three rewritten pages'
      placeholder text-only screenshots — needs provider wiring research
      similar to `filter_sql_page_chrome_test.dart`.
- [ ] 18. (docs) `export-pdf.md` — verify text against current export code;
      add `matchesGoldenFile` to `export_filter_chrome_test.dart`'s style
      picker/editor pumps if quick, else leave GIF and note as follow-up.
- [ ] 19. (docs) `generate-chart.md` — swap in existing
      `chart_action_bar_*`, `chart_glyphs_*`, `editor_column_rows.png`;
      verify chart-type list against current chart config.
- [ ] 20. (docs) `customization.md` — text-only pass; screenshot blocked on
      `home_settings_*` skip (task 21).
- [ ] 21. (app) Investigate the `home_settings_*` skip; fix or capture the
      theme picker without the language dropdown. Follow-up if not quick.
- [ ] 22. (docs) `index.md` — refresh feature grid copy if anything listed
      is gone/renamed.
- [ ] 23. (docs) `faq.md` — sanity-check against current behavior.
- [ ] 24. (docs) Final pass: `mkdocs build` locally, fix broken image refs,
      update checkboxes here.
