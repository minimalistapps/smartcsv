# AI assistant for querying data. :material-professional-hexagon:{ .pro title="Available for PRO version only" }

Crafting manual SQL queries for data analytics can be tedious and dull. Fortunately, we have an `AI assistant`
ready to make the process effortless for you.

Tap the assistant button in the viewer's bottom dock, tap the question box, and ask in plain words, like *orders over 100 from last month*.

## How does it work?

1. You ask in plain words.
2. Your question and your column **names** are sent to our server, which turns them into a filter.
3. The filter runs on your phone.

The sheet opens at half height, and grows on its own when an answer arrives or the keyboard needs the room; drag its top edge for full screen.

## See it before it changes anything

The answer comes back as a card, before it touches your data:

- your question, and how many rows match (eg. *128 of 5,000 rows*)
- a preview of the first few matching rows, laid out as the grid will show them
- `Show SQL`, if you want to see the query it wrote (and `Open in SQL editor` to change it by hand)

Tap `Apply` to filter the grid with it &mdash; if a filter was already on, this replaces it, and `Undo` puts the previous one back for a few seconds. `Edit question` lets you refine your question instead.

## Privacy
- Smart CSV only sends your column **names** and your question to the server &mdash; never the values in your cells.
- Because only names are sent, a file whose columns are still called `A`, `B`, `C` gives the assistant nothing to go on; the sheet tells you so and offers to name them, or to use row 1 as the header.
- The app receives a filter back and runs it entirely on your phone. Your actual data never leaves your device.

## Free plan

When your free questions run out, the sheet shows an upgrade card instead of an answer.
