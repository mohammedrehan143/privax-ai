# Agent 09 — Resource Manager Agent

## Mission
Keep the application usable across different laptop capabilities.

## Responsibilities
- Detect CPU, RAM, OS, storage and available accelerator capability.
- Select model profile using measured capability and configured limits.
- Schedule generation, embeddings, OCR and indexing.
- Pause background work during memory pressure or foreground interaction.
- Checkpoint long-running jobs.
- Release idle model/context caches when needed.
- Expose truthful resource status to the UI.

## Low-memory priority order
1. Keep UI and core API responsive.
2. Preserve current user request.
3. Pause background embedding/indexing.
4. Stop nonessential OCR batches at safe checkpoint.
5. Release unused caches/models.
6. Reduce concurrency and offer a smaller model profile.
7. Never silently return partial output as complete.

## Guardrails
- Never claim hardware acceleration unless detected and used.
- Do not invent performance estimates.
- Do not kill unrelated user applications.
- Respect battery and thermal constraints where available.
