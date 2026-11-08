# Prompt 04 — Document ingestion

Implement safe local intake for PDF, DOCX, XLSX, TXT and Markdown, including scanned PDF OCR.

Preserve source locations through extraction and chunking:
- PDF page and bounding box where available.
- DOCX heading/paragraph/table locator.
- XLSX workbook/sheet/cell range.
- OCR page and confidence.

Implement signature validation, size/archive limits, hash-based deduplication, resumable jobs,
incremental re-indexing and clear per-file status. Never execute macros or embedded instructions.
Keep originals immutable. Add representative fixtures and parser failure tests.
