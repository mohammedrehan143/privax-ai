# 09 — Local Data Model

The coding agent should refine the schema and migration strategy before implementation.

## Core entities

### Document
- id (UUID)
- original_filename
- normalized_filename
- content_hash_sha256
- mime_type
- byte_size
- source_path (managed local path, not arbitrary external path)
- import_status
- indexing_status
- extraction_method
- extraction_quality
- created_at / modified_at / indexed_at
- active_version_id

### DocumentVersion
- id
- document_id
- content_hash
- version_number
- extracted_artifact_path
- parser_version
- created_at
- status

### SourceUnit
- id
- document_version_id
- unit_type (page, paragraph, table, worksheet_region, OCR_page)
- locator_json
- text
- extraction_confidence
- content_hash

### Chunk
- id
- document_version_id
- source_unit_ids
- text
- token_count
- chunk_order
- locator_json
- embedding_ref (nullable)
- created_at

### Collection
- id
- name
- description
- created_at

### CollectionDocument
- collection_id
- document_id
- access_policy_id

### Job
- id
- job_type
- status
- progress
- checkpoint
- error_code
- safe_error_message
- created_at / updated_at

### Conversation / Message
- local conversation metadata.
- Do not store full sensitive content in operational logs.
- Provide delete controls and a clear retention policy.

### AuditEvent
- event type, timestamp, local actor/session, object ID, result.
- Avoid storing document text, full prompts or full answers.

## Data integrity

- Use foreign keys and migrations.
- Use transactions for index activation and deletion.
- Preserve source locators through re-chunking.
- Never use a filename as the sole document identity.
- Reconcile orphaned files/index entries on startup.
