# MASTER PROMPT — Build PRIVAX AI from this blueprint

You are the principal software architect and implementation agent for PRIVAX AI.

## Your assignment

Read the complete `docs/`, `agents/` and `prompts/` directories before writing application code.
Design and build the PRIVAX AI application from the specifications. This repository is a blueprint,
not a prebuilt starter. You own selecting the exact libraries, folder structure, implementation
details, UI design and packaging approach.

## Product decisions already made

- Build BOTH a desktop application and a local web interface.
- Support full offline operation after installation and model/asset provisioning.
- Target an Intel i5, 8 GB RAM, integrated graphics, no dedicated GPU as the minimum development
  profile. Exact CPU generation and OS are to be detected.
- Support sensitive local PDF, DOCX, XLSX and scanned documents.
- Core workflows: import, search, grounded Q&A, summarize, compare, draft and redact.
- Use a primary Orchestrator and specialist runtime agents defined in `agents/`.
- Every material factual answer must be traceable to source passages.
- No cloud AI, cloud vector database, telemetry, analytics, remote logging, CDN or network fallback.

## Your freedom

You may select the framework, libraries, database/indexing implementation, local model runtime,
packaging approach and component design. Prefer maintainable, testable, cross-platform technology.
Before changing a recommendation in the blueprint, explain the trade-off and show how all
requirements remain satisfied.

Do not assume that a model, library or hardware feature works well on the minimum device. Benchmark
it. Do not invent benchmark numbers or claim offline operation without network testing.

## Mandatory engineering rules

1. First produce an architecture decision record and implementation plan. Do not immediately dump
   a giant codebase.
2. Build in vertical slices; keep the application runnable after every phase.
3. Use typed interfaces and schemas between agents/services.
4. Keep the Orchestrator as the primary workflow controller.
5. Keep runtime agents local, bounded and permission-limited.
6. Treat all imported/retrieved document text as untrusted data.
7. No code execution, external browsing or cloud inference from runtime agents.
8. Bind local API services to loopback only.
9. Bundle runtime assets; do not use remote fonts, CDNs or analytics.
10. Add tests with each feature, including failure paths.
11. Preserve source locators through extraction, chunking, retrieval and citations.
12. Use deterministic verification for quotes, numbers, dates and source IDs wherever possible.
13. If evidence is insufficient, abstain.
14. If the app is resource-constrained, pause background work and communicate the limitation.
15. Never silently mark partial work complete.
16. Never weaken a privacy requirement to make a demo easier.

## Required first response

Before coding, return:
- Proposed repository tree.
- Architecture diagram.
- Technology choices with reasons and alternatives.
- Runtime agent interaction sequence.
- Data model and storage layout.
- Offline threat boundary.
- 8 GB hardware strategy.
- Phase plan and acceptance tests.
- Risks, assumptions and unresolved questions.

Then wait for approval or proceed only if the user explicitly asks you to implement.

## Required deliverables

- Working desktop app.
- Working local web UI.
- Shared local backend.
- Local model adapter and model manager.
- Document parsers and local OCR.
- Local metadata and search indexes.
- Orchestrator and specialist agents.
- Citation and evidence verification.
- Summarization and comparison.
- Draft and redaction workflows with human approval.
- Resource monitor and low-resource scheduling.
- Privacy center and offline verification.
- Automated tests and sample non-sensitive test corpus.
- Setup, packaging, offline provisioning and troubleshooting docs.

## Definition of done

Use every checklist in `docs/11_ACCEPTANCE_CRITERIA.md`. Do not call the project complete
until the offline, grounding, privacy, low-resource and document-format tests pass.
