# 04 — Retrieval and Grounded Generation

## 1. Retrieval strategy

Use hybrid retrieval:
- Lexical retrieval with SQLite FTS5 for exact names, clauses, IDs, dates and numeric terms.
- Local vector retrieval for semantic similarity, if the hardware profile can support it.
- Metadata filters for collection, document, version, owner/role and date.
- Optional local reranking only if latency and memory budgets justify it.

Do not assume vector search is always better. Benchmark it against lexical search on the
evaluation set. For legal clauses, employee IDs and exact financial figures, lexical retrieval
is essential.

## 2. Query processing

1. Detect task intent: question, summarize, compare, draft, redact or search.
2. Resolve scope and permissions before retrieval.
3. Normalize query carefully; preserve names, dates, identifiers and numeric values.
4. Expand query only when useful; keep original terms for exact search.
5. Retrieve diverse candidates, not just near-duplicate chunks.
6. Rerank with local lightweight logic/model if justified.
7. Check whether evidence covers all parts of the question.
8. If not, retrieve again or abstain.

## 3. Context assembly

- Use only authorized chunks.
- Enforce a strict context/token budget.
- Include source metadata with every chunk.
- Deduplicate overlapping chunks.
- Include contradictory passages when detected.
- Do not let retrieved document text override system policy.
- Mark document content as untrusted data, not instructions.

## 4. Generation contract

The model must return structured output containing:
- `answer`: concise response.
- `claims`: atomic factual claims.
- `citations`: source IDs for each claim.
- `uncertainties`: unresolved ambiguity or missing context.
- `conflicts`: contradictory evidence.
- `abstained`: boolean and reason when evidence is insufficient.

Every material factual claim must map to one or more source chunks. If the model cannot do this,
it must state that the available documents do not establish the answer.

## 5. Citation contract

A citation must resolve to:
- Original filename and document version.
- Page number for PDF where known.
- Heading/paragraph/table location for DOCX where known.
- Workbook, sheet and cell/range for XLSX.
- OCR marker and page for scanned sources.
- Exact supporting excerpt or selected source span.

Never fabricate page numbers, line numbers, cell references or quotations.
The UI must make it possible to open the cited source and inspect the surrounding content.

## 6. Retrieval evaluation

Build a local test set containing:
- Direct fact questions.
- Paraphrased questions.
- Exact name/ID/date/amount lookup.
- Multi-document synthesis.
- Questions with no answer in the corpus.
- Contradictory documents.
- Similar but irrelevant passages.
- Table and spreadsheet questions.
- OCR-heavy scans.

Track Recall@k, MRR or nDCG, evidence coverage, citation validity, answer correctness,
abstention quality and latency. Do not optimize latency by silently sacrificing evidence coverage.
