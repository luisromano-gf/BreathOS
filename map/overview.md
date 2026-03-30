# Map — Applied AI Overview

**Datestamp:** 2026-03-27  
**Version:** 0.1  
**Status:** Broad survey. Every section is a rabbit hole. Depth files to follow.  
**Coverage:** 8 clusters. Intentionally incomplete. Honest about gaps.

---

## How to read this map

This is the bird's-eye view — the world map before the city maps. It shows the major territories and how they relate. Each cluster has its own depth file in `/map/clusters/` (to be created in future sessions).

When this map is outdated, do not delete it. Create a new versioned file and log the delta in `/log`.

---

## Cluster 1: Architectures

*The substrate on which all models run.*

- **Transformer** — dominant architecture. Quadratic attention cost scales poorly with context length. Foundation of most frontier models. Battle-tested.
- **SSM / Mamba** — state space models. Linear scaling with sequence length. Strong on very long contexts. Serious challenger architecture, especially for local deployment.
- **Hybrid (Attn+SSM)** — combines transformer attention with SSM layers. Emerging fast. Seeks best of both. Watch this space.
- **Diffusion** — generative media (image, video, audio). Entirely separate paradigm from language models. Iterative denoising rather than autoregressive generation.
- **MoE (Mixture of Experts)** — sparse activation: only a subset of parameters active per token. Efficient at scale. Used in Llama 4, Qwen, DeepSeek, Mixtral.
- **RL / RLHF** — reinforcement learning from human feedback. How alignment and reasoning improvements happen post-training. Now extended to process-reward models and test-time compute scaling.

**Depth file:** `map/clusters/architectures.md` *(to be created)*

---

## Cluster 2: Model Families

### Commercial frontier (closed weights)
- **GPT-5 / o-series** (OpenAI) — strongest reasoning benchmarks. Most widely integrated via API. o3 introduced extended thinking.
- **Claude 4.x** (Anthropic) — strong on long context, honesty, instruction following. Opus for depth, Sonnet for balance, Haiku for speed.
- **Gemini 2.x** (Google) — multimodal-first. Native audio/video/image. Deep Google ecosystem integration.

### Open-weight frontier
- **Llama 4** (Meta) — MoE architecture. Scout (17B active/109B total) and Maverick (17B active/400B total). Freely deployable. Strong local inference candidate.
- **DeepSeek V3 / R1** — Chinese frontier. Matched GPT-4 class at a fraction of training cost. Geopolitical signal: frontier capability is no longer a Western monopoly.
- **Qwen 3.5** (Alibaba) — strong multilingual including Portuguese. MoE variants. Good local deployment profile.
- **Mistral** — European. Fast inference. Efficient for local and constrained environments.
- **Phi-4 / Gemma** — small but capable. Punches above weight class. Strong for edge and resource-constrained deployment.

**Key signal (March 2026):** The open-weight / closed-weight capability gap has narrowed dramatically. For many use cases, open-weight models are now sufficient or superior. Remaining gap: complex multi-step reasoning, safety alignment, and very long context handling.

**Depth file:** `map/clusters/models.md` *(to be created)*

---

## Cluster 3: Intelligence + Agency

*The phenomena that surprised everyone. Nobody predicted them. Nobody fully understands them yet.*

- **Emergence** — capabilities that appear unpredictably at scale. Not programmed. Not anticipated. A 7B model cannot do X; a 70B model can, with no explicit training for X.
- **Reasoning** — chain-of-thought, tree-of-thought, extended thinking. Models that show their work improve output quality measurably. Test-time compute scaling is now a primary research direction.
- **Agency** — goal-directed behavior across multiple steps. The model takes actions, not just answers questions. Still fragile. Still improving fast.
- **Planning** — multi-step foresight. The gap between "what should I do next" and "what sequence of actions achieves this goal." Partially solved. Open problem at scale.
- **Tool use** — calling APIs, writing and executing code, searching the web, managing files. Models that can act on the world, not just describe it.
- **Self-improvement** — models that can evaluate and improve their own outputs. Recursive capability growth. The most open and consequential question in the field.

**Depth file:** `map/clusters/intelligence-agency.md` *(to be created)*

---

## Cluster 4: Memory + Context

*Architectural decisions, not features. How a system handles memory defines its character.*

- **Context window** — the active working memory of the model. 128K to 1M+ tokens in frontier models. Hardware-constrained locally. Attention dilution is a real problem at extreme lengths.
- **RAG (Retrieval-Augmented Generation)** — retrieve relevant documents at inference time. Extends effective knowledge beyond training data and context limits. Core pattern for personal AI systems.
- **Vector DB** — Chroma, Qdrant, pgvector, Weaviate. The index that makes retrieval fast. Core infrastructure for any persistent AI system with external memory.
- **Episodic memory** — memory of past interactions. Not native to any current model. Must be engineered — typically via RAG over a structured interaction log.
- **Long context** — 1M+ token contexts in some frontier models. Theoretically replaces RAG for some use cases. Practically limited by cost, latency, and attention dilution.
- **KV cache** — key-value cache for inference. Speed and memory optimization. Architectural detail with major practical impact on local deployment.
- **Fine-tuning** — training on domain-specific data. Embeds knowledge into weights. Different tradeoff from RAG: baked in vs. retrieved. Expensive but persistent.

**Depth file:** `map/clusters/memory-context.md` *(to be created)*

---

## Cluster 5: Modalities

- **Text / LLM** — core capability. Most mature. Foundation of everything else.
- **Image** — generation (Flux, SDXL, Imagen 3) and understanding (GPT-4V, Claude, Gemini). Both mature and rapidly improving.
- **Audio** — TTS (ElevenLabs, Kokoro, Orpheus), STT (Whisper, Deepgram), music (Suno, Udio). Rapidly improving. Locally deployable TTS now available.
- **Video** — Sora-class generation (Runway Gen-3, Kling, Wan 2.1). High quality, high compute cost. Not yet practical for local generation.
- **Code** — Copilot, Cursor, Claude Code, Aider. Actively transforming software development. Probably the highest-ROI AI application for technical users today.
- **Multimodal** — any-to-any models. GPT-4o, Gemini 2.0, Claude 3.5+. Text + image + audio in a single model. Native vs. bolted-on matters significantly.

**Depth file:** `map/clusters/modalities.md` *(to be created)*

---

## Cluster 6: Deployment Patterns

- **Local inference** — Ollama, llama.cpp, vLLM, LM Studio. Run models on your own hardware. Privacy, latency, cost, and sovereignty advantages.
- **Cloud API** — OpenAI, Anthropic, Google, Groq, Together. Pay per token. No hardware. Frontier capability without local compute.
- **Agents** — autonomous execution. Model decides action sequence, calls tools, loops until goal achieved. Fragile but improving. MCP (Model Context Protocol) is emerging as a standard.
- **Orchestration** — LangChain, LlamaIndex, n8n, Dify, OpenWebUI pipelines. How models, tools, and memory are wired together.
- **Edge / IoT** — on-device inference. Phi-4, Gemma 3, quantized Llama. Offline capable. Phone-class hardware can now run capable small models.
- **Multi-agent** — multiple models collaborating. Swarms, crews, role-based teams. AutoGen, CrewAI. Emerging pattern. Still largely experimental.

**Depth file:** `map/clusters/deployment.md` *(to be created)*

---

## Cluster 7: Hardware + Network

- **GPU / CUDA** — NVIDIA dominance (RTX for local, H100/H200 for datacenter). CUDA moat is real. AMD ROCm improving but not there yet.
- **Quantization** — 4-bit (GGUF, AWQ, GPTQ), 8-bit. Trade precision for speed and memory. Essential for local deployment. 4-bit quality loss is often acceptable.
- **TPU / NPU** — Google TPUs, Apple Neural Engine, Qualcomm NPU, Intel Gaudi. Non-NVIDIA compute growing. Apple Silicon is now a serious local inference platform.
- **Distributed inference** — multi-GPU, multi-node. NCCL, tensor parallelism, pipeline parallelism. Required for models that don't fit in a single GPU's VRAM.
- **Network AI (multi-device mesh)** — interconnected personal AI nodes. Local + cloud hybrid. Distributed inference across a personal hardware fleet. Future direction.
- **Navigator's hardware** — 2× RTX 3090 (48GB VRAM total). Can run 4-bit quantized models up to ~70B parameters. Strong local inference tier. Multi-GPU tensor parallelism possible with llama.cpp / vLLM.

**Depth file:** `map/clusters/hardware.md` *(to be created)*

---

## Cluster 8: Impact Zones

### Positive
- **Science + medicine** — AlphaFold 3, drug discovery acceleration, diagnostic assistance. Possibly the highest-stakes positive impact.
- **Knowledge work** — coding, writing, research, analysis. Productivity multiplier. Uneven distribution: deep users get 10× leverage, non-users fall behind.
- **Augmentation** — human capability extended by AI. The most important design question: where does AI help vs. replace? Answer is not fixed — it shifts with capability.

### Negative / Contested
- **Labor displacement** — skills gap, role elimination, uneven benefit distribution. Real, ongoing, underaddressed.
- **AI safety** — alignment failures, misuse vectors, deepfakes, autonomous weapons. Unsolved problems with potentially high stakes.
- **Governance** — law, ethics, policy. Lagging far behind capability. Geopolitical dimension growing. EU AI Act, US executive orders, China regulation all moving fast.
- **AI sovereignty** — countries building national models (Mistral/France, Samba/Brazil, etc.). Data localization. The geopolitics of intelligence infrastructure.

**Depth file:** `map/clusters/impact.md` *(to be created)*

---

## What this map doesn't cover (known gaps)

- Specific benchmark comparisons between models (changes too fast for a static file — use engine)
- Pricing and rate limits (changes constantly — use engine)
- Individual tool deep-dives (each cluster depth file will cover these)
- The navigator's personal stack decisions (those live in `/log` as decisions)

---

*Next: deepen one cluster at a time. Start with the one most relevant to current decisions.*
