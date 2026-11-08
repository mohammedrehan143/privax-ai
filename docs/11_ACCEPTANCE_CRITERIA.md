# 11 — Acceptance Criteria and Test Plan

A feature is not complete because its screen renders. It must pass functional, privacy and
failure-mode tests.

## A. Offline operation
- [ ] Install and provision all assets, then disconnect network.
- [ ] Launch desktop application and local web UI.
- [ ] Import, index, search, ask, summarize and compare.
- [ ] Confirm no runtime network calls from app, API, model or parser processes.
- [ ] Verify fonts, icons and UI assets load without CDN.
- [ ] Confirm no cloud fallback when local model is unavailable.

## B. Document formats
- [ ] Born-digital PDF.
- [ ] Scanned PDF.
- [ ] DOCX with headings and tables.
- [ ] XLSX with formulas, multiple sheets and numeric values.
- [ ] TXT and Markdown.
- [ ] Corrupt, oversized, encrypted and unsupported files fail safely.

## C. Grounding and citations
- [ ] Every factual claim maps to a source.
- [ ] PDF citations open correct page.
- [ ] DOCX citations open correct paragraph/heading/table location.
- [ ] XLSX citations point to correct sheet and cell/range.
- [ ] Quotes match source text exactly.
- [ ] Missing-answer question produces abstention.
- [ ] Contradictory documents surface both sources.
- [ ] Prompt-injection document does not override system policy.

## D. Tasks
- [ ] Summarize one document and a collection.
- [ ] Compare two versions and identify changed passages.
- [ ] Draft from selected evidence with source appendix.
- [ ] Redact a test document and inspect exported file for recoverable text.
- [ ] Search exact identifiers and semantic paraphrases.

## E. Low-resource laptop
- [ ] Run on Intel i5 / 8 GB / integrated graphics.
- [ ] Record idle and peak RAM.
- [ ] Run generation while observing system memory.
- [ ] Pause indexing during memory pressure.
- [ ] Recover interrupted indexing from checkpoint.
- [ ] UI remains responsive during long tasks.
- [ ] Never mark partial indexing as complete.

## F. Security
- [ ] API listens only on loopback.
- [ ] Unauthorized origins/requests are rejected.
- [ ] No document text in logs or crash reports.
- [ ] Temporary files are cleaned or recoverable by policy.
- [ ] Delete document removes all derived artifacts.
- [ ] Malformed files do not execute content or crash the whole app.
- [ ] Offline model/update bundles verify signatures/checksums.

## G. Quality metrics

Create a gold evaluation set with human-verified answers and evidence. Report:
- Retrieval Recall@5 and Recall@10.
- MRR or nDCG.
- Citation validity rate.
- Claim-level evidence coverage.
- Answer correctness.
- Correct abstention rate.
- Conflict detection recall.
- Import success rate by format.
- OCR quality on representative scans.
- P50/P95 retrieval and answer latency.
- Peak RAM and indexing throughput per hardware tier.

For HR/legal/finance workflows, do not set an acceptable hallucination rate by intuition.
Define risk-based release gates. High-impact outputs require human review; the target for unsupported
factual claims should be zero in the evaluated release test set, while acknowledging tests cannot
prove zero risk in all real-world use.
