# 06 — Hardware and Model Strategy

## 1. Minimum target profile

Known initial development machine:
- Intel Core i5 (generation not yet specified).
- 8 GB system RAM.
- Integrated graphics; no dedicated GPU.

Treat this as a CPU-first, low-memory laptop. Do not assume NPU or GPU acceleration.
The OS and exact i5 generation must be detected during setup.

## 2. Hardware tiers

These are planning bands, not guaranteed performance promises. Benchmark actual devices.

### Tier 1 — constrained laptop
- 8 GB RAM, CPU inference, integrated graphics.
- Start by evaluating a 1B–1.5B quantized instruct model.
- Small context window, low concurrency, sequential model loading.
- Local embeddings may need a compact model or deferred/batched embedding.
- OCR and indexing are serialized and pausable.
- No background generation while the user is actively asking questions.

### Tier 2 — mainstream laptop
- 16 GB RAM, modern CPU, optional integrated accelerator.
- Evaluate 3B–4B quantized models.
- Larger context and modest parallelism if measurements support it.
- Hybrid lexical/vector retrieval can remain enabled.

### Tier 3 — performance laptop/workstation
- 32 GB+ RAM and capable GPU/NPU where available.
- Evaluate 7B–8B quantized models or hardware-specific variants.
- Larger context, more concurrent indexing and optional local reranker.
- All inference remains on device.

## 3. Initial model candidates

Candidates must be benchmarked for license, language support, quality, context, memory footprint,
CPU speed and offline redistribution rights before shipping.

- Generation: begin by testing a small Qwen-family instruct model in a 1B–1.5B quantized class
  for Tier 1. A 3B model is an optional experiment, not the default on 8 GB.
- Embeddings: evaluate a compact local embedding model. `nomic-embed-text` is a candidate,
  but its RAM footprint and CPU latency must be measured alongside smaller alternatives.
- OCR: Tesseract is a practical offline baseline; compare accuracy on the target languages/scans.

Do not hard-code one model name throughout the product. Use a model registry/configuration layer.

## 4. Resource manager policy

Monitor:
- Available RAM and memory pressure.
- CPU utilization and thermal/battery state where the OS exposes it.
- Free disk space.
- Model load/unload state.
- Indexing queue depth and active task.
- Optional accelerator memory/capability.

On pressure:
1. Stop accepting new background indexing work.
2. Pause OCR/embedding jobs at safe checkpoints.
3. Reduce concurrent work to one.
4. Release unused model/context caches.
5. Switch to a smaller model profile only with user-visible notice.
6. Queue user requests and explain expected delay.
7. Never return incomplete results as complete.

## 5. Benchmark plan

Measure on each tier:
- Model cold-start time.
- Tokens/second on CPU and supported accelerator.
- Peak and idle RAM.
- Embedding throughput.
- OCR pages/minute.
- Indexing time per 100 pages and per 100 MB.
- Retrieval latency and Recall@k.
- End-to-end Q&A latency.
- Battery and thermal impact for sustained workloads.

Publish measured values with device/model configuration. Do not invent benchmark figures.
