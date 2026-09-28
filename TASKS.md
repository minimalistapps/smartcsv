# Docs refresh — TASKS

Goal: `docs/*.md` (this repo) describe an old UI. The app at
`/Users/uos/Projects/SmartCsv/smartcsv` has since had a full design rework
(`DESIGN.md`, `presentation/design/*`) — new app bars, filter/SQL panel,
viewer dock, tutorial, home shell, chart editor, PDF export style editor, etc.
The docs' screenshots are old animated GIFs of the previous UI; replace them
with static PNGs captured from `flutter test --update-goldens` against the
current app, and fix any text that describes the old UI/flow.

Two repos involved:
- **App repo** (`smartcsv`): add/extend `test/design/*_test.dart` golden
  tests, regenerate `test/design/goldens/*.png`. Commit there per task.
- **Docs repo** (this one, `Docs/smartcsv`): copy the relevant PNGs into
  `docs/assets/images/`, update the markdown to reference them and correct
  any stale text. Commit here per task.

Existing golden coverage already in the app repo (reusable as-is):
- `home_recent_{light,dark}.png`, `home_recent_scrolled_*.png` — home
  screen / recent files list.
- `viewer_app_bar.png`, `viewer_app_bar_inset.png` — viewer top bar.
- `viewer_search_bar.png`, `viewer_search_bar_dark_1_5x.png` — search bar.
- `viewer_dock.png` — bottom selection dock (select/copy/etc. row).
- `viewer_how_to_use.png` — in-app help panel.
- `viewer_status_title.png` — row-count/status title.
- `tutorial_welcome_*.png`, `tutorial_intro_view_*.png`,
  `tutorial_intro_export_*.png` — onboarding screens.
- `chart_action_bar_*.png`, `chart_glyphs_*.png`, `editor_work_bar.png`,
  `editor_column_rows.png` — generate-chart screen chrome.

Known blocker: `home_settings_{light,dark}.png` golden exists in
`home_shell_test.dart` but is `skip: true` (language dropdown does a live
`google_fonts` network fetch inside the test sandbox — see comment at
`test/design/home_shell_test.dart:273`). Needed for `customization.md`;
either fix the fallback-font fetch or capture the theme picker without
opening the language dropdown.

No golden coverage yet (net-new `test/design/*_test.dart` files needed):
filter visual editor, SQL query page capture, AI assistant chat, manual
column resize + resize-all dialog, jump-to dialog, select-range dialog, copy
dialog, share/rename/remove menu, show/hide columns dialog, freeze column
dialog, column-to-image dialog, align-columns dialog, PDF export
columns/style dialogs (chrome exists in `export_filter_chrome_test.dart` but
it takes no goldens today — needs `matchesGoldenFile` calls added).

## Tasks (one commit each, in the repo noted)

- [ ] 1. (docs) Write this TASKS.md. *(this commit)*
- [ ] 2. (app) Reuse existing goldens: no new test code, just confirm
      `home_recent_*`, `viewer_app_bar*`, `viewer_search_bar*`, `viewer_dock`,
      `viewer_how_to_use`, `tutorial_*` are current (rerun suite).
- [ ] 3. (docs) `basics.md` — open file: swap in `home_recent_light.png`
      (+ note dark mode exists); fix any stale permission-flow text.
- [ ] 4. (docs) `basics.md` — search: swap in `viewer_search_bar.png`.
- [ ] 5. (app) New golden: manual column resize indicator + resize-all
      dialog (`viewer_column_resize_test.dart`).
- [ ] 6. (docs) `basics.md` — column resize: use new screenshots.
- [ ] 7. (app) New golden: jump-to dialog (`viewer_jump_test.dart`).
- [ ] 8. (docs) `basics.md` — jump to: use new screenshot.
- [ ] 9. (app) New golden: select-range dialog
      (`viewer_select_range_test.dart`).
- [ ] 10. (docs) `basics.md` — select range: use new screenshot.
- [ ] 11. (app) New golden: copy dialog + cell-detail dialog
      (`viewer_copy_test.dart`).
- [ ] 12. (docs) `basics.md` — copy: use new screenshots; reuse
      `viewer_dock.png` for the bottom action row.
- [ ] 13. (app) New golden: recent-file three-dot menu
      (share/rename/remove) (`recent_file_menu_test.dart`).
- [ ] 14. (docs) `basics.md` — share/rename/remove: use new screenshot.
- [ ] 15. (app) New golden: filter visual editor
      (`filter_visual_editor_test.dart`), light/dark.
- [ ] 16. (docs) `filter.md` — swap screenshot, verify operator list against
      `presentation/widgets/query_builder/`.
- [ ] 17. (app) Add `matchesGoldenFile` capture to
      `filter_sql_page_chrome_test.dart` (SQL editor, applied state).
- [ ] 18. (docs) `sql-query.md` — swap screenshot, verify column-alias
      explanation still matches current mapping UI.
- [ ] 19. (app) New golden: AI assistant chat screen
      (`ai_assistant_chrome_test.dart`).
- [ ] 20. (docs) `ai-assistant.md` — swap screenshot, verify privacy copy
      still matches current provider/behavior.
- [ ] 21. (app) New golden: show/hide columns dialog + freeze column dialog
      (`column_visibility_chrome_test.dart`).
- [ ] 22. (docs) `show-hide-freeze.md` — swap both screenshots.
- [ ] 23. (app) New golden: column-to-image dialog
      (`column_to_image_chrome_test.dart`).
- [ ] 24. (docs) `column-to-image.md` — swap screenshot.
- [ ] 25. (app) New golden: align-columns dialog
      (`align_columns_chrome_test.dart`).
- [ ] 26. (docs) `align-column.md` — swap screenshot.
- [ ] 27. (app) Add `matchesGoldenFile` capture to
      `export_filter_chrome_test.dart` (custom-columns sheet, style picker,
      style editor).
- [ ] 28. (docs) `export-pdf.md` — swap screenshots; reuse
      `editor_work_bar.png`/action bar pattern for the top bar.
- [ ] 29. (docs) `generate-chart.md` — swap in existing
      `chart_action_bar_*`, `chart_glyphs_*`, `editor_column_rows.png`;
      verify chart-type list against current chart config.
- [ ] 30. (app) Fix or work around the `home_settings_*` skip; capture theme
      picker.
- [ ] 31. (docs) `customization.md` — swap screenshot.
- [ ] 32. (docs) `index.md` — refresh hero copy/feature grid if any listed
      feature is gone/renamed; optionally add a tutorial screenshot.
- [ ] 33. (docs) `faq.md` — sanity-check answers still match current
      behavior (chart type list, re-import flow).
- [ ] 34. (docs) Final pass: `mkdocs build` locally to confirm no broken
      image refs, then update this file's checkboxes.

Screenshots are captured at the phone golden surface (390×844 @1x, per
`design_test_host.dart`) rather than a real device frame, matching the
existing goldens' style — consistent with each other, not with the old GIFs'
device chrome.
