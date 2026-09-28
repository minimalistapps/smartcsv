# Editing

Smart CSV edits your file right in the grid: cells, rows and columns. There is no separate editor screen and no edit mode to switch on.

## Edit a cell

- Tap a cell to select it.
- Tap it **again** to start typing in it.
- Press `Return` to save and move down one row. On the last row, `Return` adds a new row and keeps going, so you can type in data row after row.

Tapping anywhere else also saves what you typed. There is no cancel: if you change your mind, use [undo](basics.md#undo-redo).

To read a long value without editing it, tap the cell and then tap the line that shows its content above the bottom bar. A sheet opens with the whole text, a **Copy** button, and an **Edit** button.

## The Edit menu

Tap **+** in the bottom bar, or hold a row number, to open the Edit menu. What it offers depends on what is selected:

| Selected | In the menu |
|---|---|
| Nothing | Add rows… · Manage columns |
| Cells | Insert above · Insert below · Insert multiple… · Manage columns |
| Rows | Insert above · Insert below · Insert multiple… · Move rows · Delete row |
| Columns | Insert column left · Insert column right · Column type… · Manage columns · Delete column |

Holding a cell or a row number also adds **Copy**, **Cut** and **Clear content** at the top of the menu, and for a single cell, **Filter by this value**.

## Rows

### Insert rows

- Select a row and pick **Insert above** or **Insert below**.
- Select several rows (up to 50) and the menu inserts that many: select 3 rows and it says *Insert 3 rows above*.
- **Insert multiple…** opens a sheet where you choose **Above** or **Below** and how many rows, from 1 to 50.
- With nothing selected, **Add rows…** adds rows at the end of the file.

After inserting, the first new cell is selected and ready to type in. One undo removes the whole block.

### Move rows

Select the rows, tap **Move rows**, then tap the row number the rows should go after. The bar at the bottom offers **Cancel** and **Move to top** while it waits.

Rows can't be moved while the grid is sorted: the sort decides the order you see, so clear it first.

### Delete rows

Select the rows and tap **Delete row**. Smart CSV asks first, and the message after offers **Undo**.

### Cut and clear

Hold a cell, a selected range, or a row number:

- **Cut** copies the cells, then empties them.
- **Clear content** empties them. For whole rows, only the columns you can see are cleared; hidden columns keep their values.

## Columns

- **Add a column**: tap a column header, then **+** → **Insert column left** or **Insert column right**.
- **Rename a column**: tap its header, then tap the name again. You can also use **Rename** in the [Layout panel](show-hide-freeze.md).
- **Delete a column**: tap its header, then **+** → **Delete column**. Smart CSV asks first, and the message after offers **Undo**.
- **Manage columns** (from the **+** menu) is for several changes at once: drag to reorder, tap a name to rename, tap the eye to hide or show, set each column's [type](column-types.md), or delete. **Save** applies them all as one step, and one undo takes them all back.

## Saving to the file

Every edit is kept as you make it; you never lose your work by leaving the screen. The **file** on your device is only changed when you choose to.

While your edits are not yet in the file, a green **Not written to file** line shows under the row count at the top of the screen. Tap it to write the file.

- Writing asks which text encoding to use. It starts with the file's own encoding. Pick **UTF-8 with BOM** if the file will be opened in Excel.
- If only part of the file was loaded, Smart CSV never overwrites the original with that part; it writes a new file beside it instead.

!!! note
    The free version reads the first 50 rows of a file. A file with more rows opens **read-only**: you can still search, filter, sort, copy, chart and export, but not edit. Upgrading reads the whole file and unlocks editing.

!!! note
    Editing is also off until you confirm a newly opened file looks right (see [Import options](import-options.md)), and while a query you wrote yourself in [SQL](sql-query.md) is showing.
