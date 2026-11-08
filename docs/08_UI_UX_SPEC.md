# 08 — UI/UX Specification

## 1. Design direction

Professional, calm, trustworthy and productivity-focused. Avoid a flashy chatbot-only layout.
Use a dark neutral foundation with restrained cool accent colors, strong contrast and clear status.

## 2. Main navigation

- Assistant
- Documents
- Collections
- Compare
- Tasks / History
- Resource Monitor
- Privacy Center
- Settings / Model Manager

## 3. Core screens

### Dashboard / Assistant
- New question composer.
- Scope selector: all permitted documents, collection or selected files.
- Model/runtime status.
- Recent workspaces and recent tasks.
- Clear offline/local status.
- Answer panel with citations, conflicts and uncertainty.

### Documents
- Import files and folders.
- File type, size, import status, indexed status and last updated.
- Search/filter and duplicate warnings.
- Retry, pause, remove and re-index actions.
- Per-file extraction/OCR quality warning.

### Compare
- Select source and target version.
- Side-by-side or unified diff.
- Added/removed/modified labels.
- Evidence links to both versions.
- Export only after review.

### Resource Monitor
- RAM available/used.
- CPU utilization.
- Disk space.
- Model loaded and memory footprint where measurable.
- Active indexing/OCR jobs.
- Pause/resume controls and low-resource mode.

### Privacy Center
- Explicit statement of local processing.
- Local data directory.
- Network status / last verified offline test.
- Retention and deletion controls.
- Export and backup guidance.
- Logs/diagnostics preview with redaction.

## 4. Interaction rules

- Never imply a file is indexed until indexing completes and validation passes.
- Distinguish “offline-ready” from “currently offline”; do not claim either without checks.
- Show progress and allow cancellation for long tasks.
- Display citations inline and in a source panel.
- Make uncertainty visible, not hidden in a tooltip.
- Use accessible keyboard navigation, focus states and screen-reader labels.
- On small screens, retain the key actions; do not simply shrink desktop tables.
