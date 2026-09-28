# Show column image url as an image

Transforming your CSV data, especially when it includes image URLs, into a visually appealing display has never been easier. Smart CSV can show a column of image URLs as actual images, by setting that column's **type** to **Image**.

Here's how you can do that:

- Tap the column's header to select it.
- Tap **Layout** in the bottom bar, then **Type**.
- In the type sheet, pick **Image**. Smart CSV shows how many of the column's values fit that type before you apply it.
- Tap **Apply**. Every cell in the column now shows a thumbnail of the image at that URL, and you can type or paste a new address directly into a cell.

=== "Layout → Type"
    ![The Layout panel for a selected column](assets/images/smartcsv-layout-panel-column.png){ width="300" loading=lazy }

!!! note
    This is one of several column types Smart CSV supports (`Text`, `Number`, `Checkbox`, `Select`, `Date`, `Link`, `Image`) &mdash; see [Column types](column-types.md) for all of them. Choosing a type never changes the text stored in your file; it only changes how the column looks, sorts and filters.
