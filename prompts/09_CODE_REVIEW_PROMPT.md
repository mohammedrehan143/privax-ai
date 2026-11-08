# Prompt 09 — Continuous code review

Review every implementation change for:
- Blueprint compliance.
- Correct agent boundaries and Orchestrator ownership.
- Data provenance and citation integrity.
- Offline-only execution and loopback binding.
- Resource limits and cancellation.
- Error handling and honest task status.
- Security of file parsing, temporary storage and logs.
- Test coverage for normal, failure and adversarial paths.
- Maintainability, type safety and migration safety.

Return blocking issues first. Do not rewrite unrelated code. Require a regression test for each
bug fixed.
