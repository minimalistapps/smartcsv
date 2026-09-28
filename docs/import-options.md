# Import options

When you open a CSV file, Smart CSV works out how it is written: the separator (comma, semicolon, pipe, tab or colon), the quote character, and the text encoding. Besides UTF-8 and UTF-16 it recognises the encodings older spreadsheet apps save in &mdash; Western and Central European, Cyrillic, Vietnamese, Japanese (Shift_JIS, EUC-JP), Chinese (GB18030/GBK) and Korean (EUC-KR). A first line such as `sep=;` sets the separator explicitly.

## Does this look right?

The first time you open a file, it opens read-only, with a card at the bottom asking **Does this look right?** The card says what was detected, for example *Separator Semicolon · Header row · 12 columns · 3,400 rows*. Scroll the table and check the columns are split where you expect.

- **Looks right** unlocks [editing](editing.md). The file is always read this way from now on, and writing it back keeps the same separator and encoding.
- **Adjust** opens the import options (below).

If some rows don't look like the rest, the card says so, for example *12 rows have a different number of columns, first at row 340*. That usually means the separator or quote character is wrong.

You can still search, sort, filter and change the layout while the card is up. The card comes back whenever the file is read from scratch: after you change the import options, or when the file changed on your device since it was last opened.

## Change the import options later

Open the file, tap :material-dots-vertical: at the top right, then **Import options**. If you have edits that aren't written to the file yet, Smart CSV warns you first, because importing again replaces them.

For a SQLite database the entry is **Choose table** instead: pick another table, check the preview, and tap **Import**.

## The options

The sheet has the options at the top and a live **Preview** of the first rows below. Change anything and the preview updates.

- **Separator** &mdash; Comma, Semicolon, Tab, Pipe, Colon or Space. The detected one has a small wand icon. **Other** lets you type your own single character (for example `~`), or `\t` for a tab.
- **First row is the header** &mdash; turn this off when the file has no header line. The columns are then named `A`, `B`, `C`…
- **More options**:
    - **Quote character** &mdash; `"` or `'`, the character that wraps cells containing the separator.
    - **Encoding** &mdash; pick another one if letters in the preview look garbled. A line above the preview says when some characters can't be read with the encoding you chose.
    - **Comment lines** &mdash; lines starting with this character (`#` by default) are skipped. Choose **None** to read every line.
- **Reset to detected** puts everything back to what Smart CSV detected.

The preview also warns when the settings look wrong, and offers the fix as a button &mdash; for example *The rows split evenly with Semicolon.* **Use Semicolon**. Nothing changes until you tap it.

## Files without a header row

When a file is read without a header row, its columns are called `A`, `B`, `C`… and shown greyed and in italics.

- **If row 1 is really the header**, Smart CSV offers **Use row 1 as header**. You can also do it yourself from the **+** menu or **Manage columns**.
- **To name a column**, tap its header, then tap the name again. The first time, Smart CSV asks where to keep the names: **Add header row** writes them as the file's first line next time you write it; **Keep in SmartCsv only** leaves the file as it is.

The [AI assistant](ai-assistant.md) only sees column names, so it works much better once columns are named.

## Good to know

- Blank lines show as empty rows and are written back as blank lines.
- Spaces at the start and end of each cell are removed.
- A cell can hold up to 100,000 characters. If one is longer, it's almost always a quote that never closes; the import options open with the line it happened on so you can fix the quote character or separator.
