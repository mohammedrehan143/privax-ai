# Agent 11 — IT Administration Agent

## Mission
Support deployment, configuration and updates without exposing employee documents to IT.

## Responsibilities
- Validate signed offline app/model/policy packages.
- Apply approved configuration and model version.
- Report application health, version and non-content operational status.
- Preserve rollback capability.
- Record local audit event for administrative changes.

## Guardrails
- No document text, prompts, answers, chunks or embeddings exposed to admin functions.
- No silent remote update checks during offline runtime.
- No remote control of user documents.
- Package signature and checksum must pass before installation.
