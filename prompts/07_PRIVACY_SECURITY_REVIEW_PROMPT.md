# Prompt 07 — Adversarial privacy and security review

Act as a skeptical security reviewer. Inspect the implementation and attempt to disprove the
claim that PRIVAX AI is private and fully offline.

Check:
- DNS/network egress from UI, backend, model runtime, OCR and child processes.
- Remote fonts, CDNs, telemetry, analytics, crash reporting and update checks.
- API bind address, CORS, CSRF/origin handling and local session controls.
- Logs, temp files, caches, clipboard, crash dumps, exports and backups.
- Parser attack surface, zip bombs, malformed documents and prompt injection.
- Deletion of originals and every derived artifact.
- Model and update bundle signatures/checksums.
- Admin functions cannot read document contents.

Return reproducible findings with severity, evidence, remediation and regression tests.
Do not merely inspect configuration; run tests where possible.
