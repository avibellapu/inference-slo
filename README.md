# inference-slo

Self-hosted LLM inference is easy to get running and hard to run reliably. Spinning up vLLM with a model on a GPU takes an afternoon — but most tutorials stop there. They don't answer the questions that actually matter in production: What's your P99 time-to-first-token under load? What happens when a GPU node dies mid-request? How do you autoscale on a signal that isn't just CPU/memory, when the real bottleneck is KV cache capacity? What's your blast radius when a bad deploy ships a broken quantized model?

inference-slo treats self-hosted inference as an SRE problem, not a deployment problem. It's a self-hosted LLM platform on Kubernetes/EKS with defined latency SLOs, GPU-aware autoscaling, health/readiness probing tuned for inference workloads (not generic HTTP checks), and full observability into the metrics that matter for LLM serving — TTFT, inter-token latency, and throughput — not just uptime.

The goal isn't a novel serving engine. It's applying the operational rigor of production infrastructure — the kind you'd expect for any customer-facing service — to a class of workload that's still mostly treated as a research artifact.