# Prompt 05 — Orchestrator and RAG

Implement the Orchestrator as the only workflow planner and dispatcher.

Build:
- Intent classification and bounded task plans.
- Permission checks before retrieval.
- FTS lexical retrieval and measured local vector retrieval.
- Metadata filtering and deduplication.
- Context/token budgeting.
- Structured answer schema with claim-level source IDs.
- Verification agent checks for source existence, quote exactness, numeric/date consistency,
  locator validity, conflict and evidence coverage.
- One bounded retry; then abstain or return partial with clear status.

Test answerable, unanswerable, contradictory, paraphrased, exact-ID and prompt-injection cases.
