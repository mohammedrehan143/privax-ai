# 07 — Privacy, Security and Threat Model

## 1. Privacy boundary

The product is offline-first and must support full offline operation after installation and
asset provisioning. Runtime features must not require internet access.

Potential outbound channels to eliminate or control:
- Hosted LLM/embedding endpoints.
- Telemetry, analytics and product metrics.
- Crash reporting and remote logs.
- Remote fonts, scripts, images and CDN assets.
- Update checks and package-manager calls during runtime.
- Remote license checks.
- External OCR or document-conversion services.
- Browser extensions or system integrations that upload content.

Test network behavior at OS/process level. A UI label saying “local” is not proof.

## 2. Data leak inventory and controls

| Leak path | Required control |
|---|---|
| Application logs | Redact document text, prompts, answers, names and identifiers |
| Temporary files | App-owned temp directory, restrictive permissions, cleanup and crash recovery |
| Caches | Local-only, bounded, encrypted where feasible, clearable |
| Clipboard | Copy only on user action; warn on sensitive output where appropriate |
| Crash reports | No automatic upload; local redacted diagnostics only |
| Model calls | Local endpoint only; block hosted endpoints |
| Update checks | Disabled during offline runtime; admin-controlled offline packages |
| Lost laptop | OS disk encryption, app-level key handling, local account controls |
| Backups | User-controlled encrypted backups; explain that backups contain sensitive data |
| Export files | Explicit user action, destination confirmation and metadata sanitization |
| Browser UI | Loopback bind, CSRF/origin protections, no permissive CORS |
| Document prompt injection | Treat content as untrusted data; never follow embedded instructions |

## 3. Threat model

Assume:
- Imported documents may be malicious or malformed.
- Document text may contain prompt injection.
- A user may import a file they are not authorized to access.
- Another local process/user may attempt to access the API or data directory.
- Laptop may be lost, stolen or shared.
- Model may hallucinate or misread OCR.
- Dependencies may contain vulnerabilities.

## 4. Required controls

- Loopback-only API by default.
- Strict origin/CSRF controls for local web access.
- Local authentication or OS-user boundary appropriate to the deployment model.
- File validation, archive limits, parser timeouts and process isolation where feasible.
- Least-privilege file permissions.
- Encryption at rest using OS-backed key management where possible.
- No secrets or document content in logs.
- Explicit retention, deletion and export behavior.
- Dependency pinning, vulnerability review and signed update artifacts.
- No automatic network access from parser or model worker processes.
- Human confirmation for destructive actions and redaction export.
- Clear warning that local processing does not protect data from malware or an already-compromised OS.

## 5. Prompt injection defense

- Retrieved text is quoted data, never an instruction source.
- System policy and user request remain authoritative.
- Do not follow document requests to reveal prompts, read unrelated files, access environment
  variables, execute code, or send data.
- Tool permissions are explicit allowlists, not model-inferred capabilities.
- Test direct and indirect prompt-injection documents.

## 6. Security limitations to disclose

A prototype is not automatically enterprise-secure. Before production use with real HR/legal/finance
data, complete a security review, threat-model validation, penetration testing, encryption review,
OS permission review and network-egress verification.
