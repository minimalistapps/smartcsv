# FAQ
---

### Which chart types are supported?

Currently, Smart CSV Viewer support column chart, bar chart, line chart, area chart, spline chart, scatter chart, step line chart, step area chart, pie chart, doughnut chart, and pyramid chart. See [Generate chart](generate-chart.md) for which are Pro.

### What do you mean by “customizable”?

In Smart CSV Viewer you can custom as much as you can. For example, when you only want to copy a part of data in a row, you can use the “filter” feature to exclude it. You can extract data by column. When you export to a pdf file, you can custom the style (color scheme) to match your expectation. More than a CSV converter tool, now you can change the look of your pdf file by styling it.


### Why my file not being updated?

Opening a file imports it into a local database once; that's why reopening it is instant, and why you can run SQL queries against it. If the file changes on disk after that, Smart CSV notices automatically the next time you open it:

- If you hadn't edited it in the app, it's re-imported for you.
- If you had edited it in the app, you're asked once whether to **Reload** (discard your edits and import the new file) or **Keep my edits**.

There's no manual re-import step for a changed file &mdash; only the `Import options` in the viewer's `⋮` menu, which is for re-reading the same file with different settings (headers, delimiter, encoding), not for picking up external changes.
