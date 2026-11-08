# Prompt 06 — Task agents

Implement summarization, comparison, drafting, redaction and search workflows according to
`docs/05_TASK_WORKFLOWS.md` and their agent specifications.

Each task:
- Has typed inputs and outputs.
- Operates only on authorized local evidence.
- Preserves source provenance.
- Reports uncertainty and partial completion.
- Has unit and integration tests.

Redaction must preserve the original and require explicit approval before export. Drafting must
never send or publish content. Comparison must identify both versions and cite both sides.
