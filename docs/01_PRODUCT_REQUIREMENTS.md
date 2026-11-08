# 01 — Product Requirements

## 1. Product vision

PRIVAX AI is a private document workbench for employees who need AI assistance over sensitive
business files but cannot send those files to public cloud AI services.

The product should feel like a focused desktop productivity tool, not a generic chatbot.
The same workspace is available as:
1. A native desktop application.
2. A local web interface accessible only from the user's own device by default.

Both interfaces use the same local backend, local model runtime, local document store and
policy engine. They must not create separate data pipelines.

## 2. Users and jobs to be done

### HR business partner
- Search salary, appraisal and performance documents.
- Summarize employee-specific records.
- Compare review periods.
- Draft a private HR note from selected evidence.
- Apply role and document access restrictions.

### Legal associate
- Compare vendor contract versions.
- Find clauses, dates, obligations and termination conditions.
- Identify missing or conflicting language.
- Draft a review checklist with source references.

### Finance analyst
- Search quarterly reports and spreadsheets.
- Summarize financial results.
- Compare periods and workbook versions.
- Trace each number to a workbook, sheet and cell/range where possible.

## 3. Required capabilities

### Document intake
- PDF (born-digital and scanned)
- DOCX
- XLSX
- TXT and Markdown
- OCR for scanned pages and image-based PDFs
- Batch import with progress and per-file status
- Duplicate detection using cryptographic hashes
- Re-index when a file changes
- Preserve original files; never silently overwrite them

### Document understanding
- Full-text search
- Natural-language Q&A
- Summaries at document and selected-section level
- Compare two or more versions
- Extract key entities, dates, amounts and obligations as evidence-backed candidates
- Redaction workflow with preview and explicit confirmation
- Drafting based only on selected/retrieved evidence

### Trust and review
- Citation on every material factual claim in generated answers.
- Citation opens the exact source location where supported.
- Display source filename, page/sheet, section and excerpt.
- Show when evidence is insufficient.
- Surface contradictory evidence rather than selecting one silently.
- Distinguish extracted text from model-generated interpretation.
- Allow users to flag incorrect extraction or answer.

### Device and administration
- Detect CPU, RAM, OS, available storage and accelerator capability where possible.
- Select a suitable local model profile.
- Resource monitor and low-resource mode.
- Local model management and offline model import.
- Local-only user profiles and document collections.
- Export audit events without document content.
- IT-managed configuration and offline update package support.

## 4. Out of scope for the first release

- Sending files to cloud AI as fallback.
- Training a foundation model.
- Full enterprise document-management replacement.
- Automatic email sending or external actions.
- Cross-device cloud sync.
- Unreviewed automated legal, HR or financial decisions.
- Remote administration that can read document contents.

## 5. Product principles

1. Privacy by default, not a settings toggle.
2. Evidence before fluency.
3. Abstention is better than a confident unsupported answer.
4. Small-device support is a product requirement.
5. Human review for consequential output.
6. Clear status: indexed, partially indexed, failed, stale or ready.
7. User control over import, deletion, redaction and export.
