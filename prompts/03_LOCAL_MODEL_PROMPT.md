# Prompt 03 — Local model and resource profiles

Implement the local model adapter and hardware-aware model manager.

Minimum target: Intel i5, 8 GB RAM, integrated graphics, CPU-first.

Tasks:
- Detect OS, CPU, RAM and available storage; detect GPU/NPU only where reliable.
- Define model registry with model ID, version, quantization, license, checksum and hardware tier.
- Benchmark candidate small instruct models; begin testing 1B–1.5B quantized class on Tier 1.
- Evaluate compact local embedding model separately.
- Implement model load/unload, timeout, cancellation and memory limits.
- Never use hosted inference or cloud fallback.
- Make model absence a clear recoverable state.
- Add offline tests that prove requests remain local.
- Do not claim performance until measured on target hardware.
