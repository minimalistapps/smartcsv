# Docs refresh — TASKS

## What changed since this was first written

Reading the app's own `docs/*.md` (dev specs, at
`/Users/uos/Projects/SmartCsv/smartcsv/docs/`) turned up more than a visual
refresh: the interaction model changed.

- The **five column dialogs** the public docs described (resize, freeze,
  align, column-to-image, show/hide columns —
  `column_resize_dialog.dart`, `freeze_column_dialog.dart`,
  `column_align_dialog.dart`, `column_to_image_dialog.dart`,
  `csv_columns_selection_dialog.dart`) belong to the **old grid**, which is
  dying (`viewer-layout-panel.md`). The current grid replaces all five with
  one **Layout panel**: tap a column header, then Width / Align / Sort /
  Freeze / Type / Hide live in a panel over the grid.
- **Show as image** is gone as a standalone action; it is now a column
  **Type** (`column-types.md`) alongside Text/Number/Checkbox/Select/
  Date/Link/Image.
- **Filter** is a panel over the grid with **Filter** and **Sort** tabs
  (`filter-sheet.md`, `sorting.md`), not a full-screen editor. SQL lives
  inside it as **Edit as SQL**, not a separate screen/tab.
- **Copy** is one tap in the bottom dock (no column-picker dialog). Cut,
  Clear content, and per-cell **Filter by this value** are on a long-press
  menu (`cell-content.md`).
- **Jump to row** and **select a range** still exist as dialogs, but moved
  from bottom-bar buttons into the viewer's `⋮` menu
  (`csv_viewer_more_actions.dart`) — which also now holds **Chart** and
  **Export PDF**, moved off the top bar to make room for undo/redo.
- **Sort**, **Undo/redo**, and the **selection summary** (count/sum/avg
  over a selection) are real, current features that had no page in the
  public docs at all.
- The **AI assistant** is a sheet reached from the dock (one answer card
  per question), not a chat screen.
- The **6-color theme picker** `customization.md` described is gone;
  settings now only has Dark/Light/System and Language.

## Done this session

Two repos: **app repo** (`smartcsv`) got new `test/design/*_test.dart`
golden tests + regenerated `test/design/goldens/*.png`; **docs repo** (this
one) got the matching `docs/*.md` rewrites and PNGs copied into
`docs/assets/images/`. Each item below is its own commit in the repo(s)
noted.

- [x] `TASKS.md` written, then revised after auditing the app's specs.
- [x] Confirmed pre-existing goldens (`home_recent_*`, `viewer_app_bar*`,
      `viewer_search_bar*`, `viewer_dock`, `viewer_how_to_use`,
      `viewer_status_title`, `tutorial_*`, `chart_action_bar_*`,
      `chart_glyphs_*`, `editor_work_bar`, `editor_column_rows`) still pass.
- [x] (app) New golden: the viewer's `⋮` menu (`viewer_more_menu_test.dart`).
- [x] (app) New golden: the recent-file share/rename/remove sheet
      (`recent_file_menu_test.dart`).
- [x] (app) New golden: the filter panel's SQL editor
      (`sql_query_screenshot_test.dart`), using the docs' own
      Year/Revenue/Expensive example.
- [x] (app) New golden: the visual filter editor
      (`filter_visual_editor_test.dart`).
- [x] (app) New golden: the settings screen's dark-mode row
      (`settings_appearance_test.dart`) — sidesteps the pre-existing
      `home_settings_*` skip (language dropdown does a live `google_fonts`
      fetch in the test sandbox, `home_shell_test.dart:273`).
- [x] (docs) `basics.md` — rewritten: selection model, `⋮` menu for
      jump/select-range, Layout panel for column width, one-tap copy +
      long-press menu, added Sort and Undo/redo sections.
- [x] (docs) `filter.md` — rewritten for the filter panel.
- [x] (docs) `sql-query.md` — rewritten: SQL lives inside the filter panel.
- [x] (docs) `ai-assistant.md` — rewritten for the dock sheet; no new
      screenshot (see Follow-up).
- [x] (docs) `show-hide-freeze.md`, `align-column.md`, `column-to-image.md`
      — rewritten for the Layout panel / column types; no new screenshots
      (see Follow-up).
- [x] (docs) `export-pdf.md`, `generate-chart.md` — updated entry point
      (`⋮` menu) and the chart dock's Title/Type/Size changes.
- [x] (docs) `customization.md` — rewritten (theme picker removed).
- [x] (docs) `faq.md` — fixed the chart-type list and the re-import answer.
- [x] (docs) `index.md` — checked against the current feature set; no
      change needed.
- [x] `mkdocs build` run locally — no broken refs, no new warnings beyond
      the repo's pre-existing (unrelated) emoji-extension deprecation
      warnings that make `--strict` fail regardless of this work.

## Follow-up (not done this session)

- **Layout panel golden.** `show-hide-freeze.md`, `align-column.md`, and
  `column-to-image.md` have accurate text but no screenshot.
  `LayoutPanel` needs `contentProvider` (real document content),
  `gridSelectionProvider` and several column-mutation view models — real
  provider wiring against a loaded document, not a hand-composable widget
  like `FilterTree`. Worth doing once, since it covers three pages at once.
- **AI assistant sheet golden.** `bot_dialog.dart` pulls in network
  (`dio`), IAP (`purchases_flutter`) and the CSV storage view model — too
  much to wire safely in one sitting. `ai-assistant.md` is text-only.
- **`home_settings_*` skip.** Root cause is `language_config.dart`'s
  `GoogleFonts.openSans()` call per dropdown item; `customization.md`'s
  screenshot sidesteps it, but the underlying golden gap (and whatever
  makes the fetch happen despite `allowRuntimeFetching = false`) is still
  open.
- **Old GIFs still on disk** under `docs/assets/images/` for pages this
  session didn't touch visually (or that no longer have any image), e.g.
  `smartcsv-export-pdf.gif`, `smartcsv-generate-chart.gif` (kept as a
  fallback illustration where the flow itself didn't change), and the now
  fully unreferenced `smartcsv-copy.gif`, `smartcsv-jump.gif`,
  `smartcsv-select-range.gif`, `smartcsv-share-rename.gif`,
  `smartcsv-show-hide-columns.gif`, `smartcsv-column-to-image.gif`,
  `smartcsv-align-column.gif`, `smartcsv-manual-resize.gif`,
  `smartcsv-resize-auto.gif`, `smartcsv-visual-filter.gif`,
  `smartcsv-sql-query.gif`, `smartcsv-ai-assistant.gif`. Safe to delete
  once someone's confirmed nothing external links to them directly.
