# 10 — IT Operations and Updates

## Deployment modes

### Individual laptop
- Install desktop application and local model runtime.
- Provision model assets during setup.
- App starts local services on demand.
- No document content leaves the laptop.

### Managed organization deployment
- IT distributes signed application and model bundles.
- Policy bundle can set approved model versions, storage location, retention and disabled features.
- IT can update app/model/policy without access to document contents.
- Device reports only minimal operational status if an organization explicitly enables it;
  default product behavior remains no telemetry.

## Offline update design

1. Build release package in a controlled environment.
2. Sign package and generate checksums.
3. Transfer through approved offline media/process.
4. Verify signature and checksum locally.
5. Stage update and preserve rollback.
6. Apply update without reading document contents.
7. Record version and result in local audit log.

## Model lifecycle

- Model registry records name, version, quantization, license, checksum, size and hardware profile.
- Import model from approved local bundle.
- Verify checksum before installation.
- Keep model files read-only after installation where possible.
- Provide uninstall and disk-space controls.
- Do not silently replace a model or change its license/version.

## IT cannot inspect documents

Administration APIs may expose:
- Application version.
- Model version.
- Device capability profile.
- Service health.
- Indexing job counts and error categories without content.
- Policy version and update status.

Administration APIs must not expose:
- Document names unless explicitly required and authorized.
- Extracted text, chunks, embeddings or prompts.
- User questions or generated answers.
- Document contents or source excerpts.
