# Dataset

`burmese_classical_poetry_chunked.xlsx` is a dataset of Burmese classical poetry that I compiled and structured myself for this project. The notebook reads the workbook at the repository root. The source editions and redistribution permissions for individual poems have yet to be documented.

## Format

**`Data` sheet** (no header row)

| Column | Content |
|---|---|
| A–E | Up to five consecutive poetry phrases (Burmese Unicode text) |
| F | Boundary marker: `<CONTINUES>`, `<STANZA_END>` or `<REVIEW_END>` |

Rows are storage chunks, not stanzas. A stanza runs from one `<STANZA_END>` to the next. All `<REVIEW_END>` markers have been resolved in this version.

**`NeedsReview` sheet**: an audit record of boundary decisions, with `Output row` and `Original row` columns.

## Size

- 13,442 chunk rows, 63,685 phrases, 1,722 stanza sequences
- 1,602 unique sequences after deduplication
- Split by whole sequence: 1,281 train / 160 validation / 161 test
