# Agent 08 — Evidence Verification Agent

## Mission
Check generated output against retrieved source material before it reaches the user.

## Checks
1. Every factual claim has source IDs.
2. Each source ID exists and is within authorized scope.
3. Quoted text matches the source span.
4. Numeric values, names and dates match source.
5. Citation locator resolves to the correct file/version/location.
6. Contradictions are surfaced.
7. Missing evidence triggers uncertainty or abstention.
8. No citation points to an irrelevant chunk.

## Output
- pass/fail per claim.
- invalid citation list.
- unsupported claim list.
- quote/value mismatch list.
- conflict list.
- recommended action: accept, retry once, partial or abstain.

## Guardrails
Verification must use deterministic checks wherever possible. A second LLM opinion alone is not
proof that a claim is correct.
