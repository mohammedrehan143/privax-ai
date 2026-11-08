# 05 — Task Workflows

## Ask questions
- Retrieve evidence from the selected scope.
- Answer with claim-level citations.
- Show source excerpts and conflicts.
- Abstain if evidence is absent or inadequate.

## Summarize
- Let user choose document, section or collection scope.
- Use hierarchical summarization for long documents: section summaries, then synthesis.
- Keep each material claim linked to source locations.
- Label executive interpretation separately from document facts.

## Compare versions
- Require explicit source versions or a clear selection.
- Align headings/clauses/paragraphs/tables.
- Classify changes: added, removed, modified, unchanged, uncertain alignment.
- Quote both old and new source locations.
- Never infer legal significance as a definitive conclusion; label potential impact for human review.

## Draft
- Ask for output purpose and intended audience when essential.
- Build a draft only from selected evidence and explicit user-provided instructions.
- Cite factual statements in the draft or provide a source appendix.
- Clearly mark placeholders and unsupported details.
- Never send or publish the draft automatically.

## Redact
- Identify candidate sensitive spans locally.
- Show a preview with category and source location.
- Require explicit confirmation before creating a redacted copy.
- Preserve original unchanged.
- Use irreversible redaction in exported copies; do not merely draw a black rectangle over text.
- Warn that metadata, hidden layers, comments and OCR text can leak content if not sanitized.

## Search
- Provide exact and semantic search modes.
- Show matching excerpt, source location and match type.
- Respect document access restrictions before showing snippets.
