# Awesome Agentic AI Waifus & Companions

> A one-stop, opinionated map of the open-source AI companion / "agentic waifu" ecosystem — frameworks, full-stack projects, models, embodiment tech, communities, people, and the media that inspired all of it.

This list focuses on **open source** and **freely available** projects, papers, and guides for building agentic AI companions — local-first chatbots-with-a-body that remember you, look like something, sound like something, and (increasingly) act on their own initiative. It deliberately avoids listing closed, proprietary companion apps (Character.AI, Replika, Kindroid, etc.) except where they've published genuinely useful research, specs, or educational material. See [Adjacent Reading](#adjacent-reading-not-strictly-open-source) for the few exceptions.

Within each section, entries are roughly ordered by **importance/maturity** (GitHub stars, ecosystem centrality, how load-bearing the project is), not alphabetically — the thing you should look at first is at the top. ★ counts are GitHub stars as of **November 2026** and drift quickly; treat them as a rough signal of scale, not a ranking.

**Disclosure of bias:** I am the author of [**YuriOS**](#yurios--my-project) and the accompanying book [**The Agentic Waifu Codex**](#yurios--my-project), which are included below in their own clearly-marked section. I've tried to be honest about where they sit relative to the rest of the field rather than overselling them — judge for yourself.

Contributions/corrections welcome — this is a living document. See [CONTRIBUTING.md](CONTRIBUTING.md).

*Last reviewed: November 2026.*

---

## Table of Contents

- [Prior Art (the lists this one stands on)](#prior-art-the-lists-this-one-stands-on)
- [YuriOS — My Project](#yurios--my-project)
- [Full-Stack AI Companion / AI VTuber Projects](#full-stack-ai-companion--ai-vtuber-projects)
- [Agentic AI Frameworks](#agentic-ai-frameworks)
- [Memory & Long-Term Context](#memory--long-term-context)
- [Local LLM Inference & Serving](#local-llm-inference--serving)
- [Open / Roleplay-Tuned Language Models](#open--roleplay-tuned-language-models)
- [Voice: Text-to-Speech](#voice-text-to-speech)
- [Voice: Speech-to-Text & Turn-Taking](#voice-speech-to-text--turn-taking)
- [Embodiment: Avatars, VTubing & Motion](#embodiment-avatars-vtubing--motion)
- [Image & Video Generation](#image--video-generation)
- [Character Formats & Persona Standards](#character-formats--persona-standards)
- [Character Card Explorers & Repositories](#character-card-explorers--repositories)
- [Frontends & Chat Clients](#frontends--chat-clients)
- [Fine-Tuning, Datasets & Synthetic Data](#fine-tuning-datasets--synthetic-data)
- [Papers, Guides & Reading](#papers-guides--reading)
- [Communities & Websites](#communities--websites)
- [Creators & Showcases](#creators--showcases)
- [Adjacent Reading (not strictly open source)](#adjacent-reading-not-strictly-open-source)
- [AI-Waifu-Adjacent Media: Anime, TV, Film & Books](#ai-waifu-adjacent-media-anime-tv-film--books)

---

## Prior Art (the lists this one stands on)

This list exists in a small genre. Read these too — they overlap with this one but each has a different center of gravity.

- **[proj-airi/awesome-ai-vtubers](https://github.com/proj-airi/awesome-ai-vtubers)** ★522 — the densest single catalog of AI VTuber codebases (streaming-first: Bilibili/Twitch/YouTube integration, Live2D). Maintained by the team behind AIRI.
- **[parallelarc/Awesome-AI-Waifu](https://github.com/parallelarc/Awesome-AI-Waifu)** ★21 — companion-first rather than streaming-first; good frameworks/infrastructure split.

<sub>[↑ back to top](#table-of-contents)</sub>

---

## YuriOS — My Project

*(Flagged up front per the disclosure above — take the framing with a grain of salt, but the code and book are real and free.)*

- **[YuriOS](https://github.com/yuri-os/YuriOS)** ([yurios.org](https://yurios.org)) ★44 — An always-on, local-first, Apache-2.0 AI companion runtime. Its focus is the **mind**: a continuously running cognitive loop (sense → appraise → decide → act → reflect → regulate) that gives the companion its own goals, consolidates memory overnight ("dreaming"), tracks promises it's made to you, edits its own persona over time, and uses a conservative two-gate salience model to decide when it may message you unprompted. VRM or Live2D body; faster-whisper + Kokoro-82M/GPT-SoVITS + Silero VAD voice loop; everything it knows is stored as plain markdown in a git-backed "Vault" on your own disk. No account, no telemetry, any LLM backend via LiteLLM — a local GPU is optional if you point it at a hosted API.
- **[The Agentic Waifu Codex](https://yurios.org/book/)** (aka *Building Agentic Waifus*) — a free, 465-page, 45-chapter practitioner's book: character design and lore, memory/RAG/agentic architecture, voice and avatar embodiment, five runnable reference implementations that build up to YuriOS itself, and the creator-economy/monetization side most technical guides skip. [PDF releases](https://github.com/yuri-os/AgenticWaifuCodex/releases/latest) · [source](https://github.com/yuri-os/AgenticWaifuCodex). Its appendices (tools/stacks, reading list, communities) fed directly into this list — if you want the long-form version of this document's reasoning, that's where it lives.

Where YuriOS sits relative to its nearest neighbors, honestly: **[AIRI](https://github.com/moeru-ai/airi)** has a much bigger community, ships further along the streaming/gaming axis (Minecraft, Factorio), and is the more mature *product*. **[z-waif](https://github.com/SugarcaneDefender/z-waif)** and **[Soul of Waifu](https://github.com/jofizcd/Soul-of-Waifu)** are more turnkey if you just want a working local waifu today. YuriOS's bet is narrower and specifically about the always-on autonomy/mind loop — if that's not what you're after, one of those three is probably the better starting point.

<sub>[↑ back to top](#table-of-contents)</sub>

---

## Full-Stack AI Companion / AI VTuber Projects

Complete, runnable companion/VTuber applications — pick one of these if you want something working end-to-end rather than assembling a stack yourself. (Looking for SillyTavern? It's under [Frontends](#frontends--chat-clients); ElizaOS is under [Agentic AI Frameworks](#agentic-ai-frameworks).)

- **[AIRI](https://github.com/moeru-ai/airi)** ★51k — "A container of souls of AI waifu." Self-hosted, cross-platform (Web/macOS/Windows) companion with realtime voice chat and the ability to actually play games (Minecraft, Factorio). The most complete and actively developed project in this space; explicitly aimed at "Neuro-sama's altitude." Best single reference implementation to study.
- **[Open-LLM-VTuber](https://github.com/Open-LLM-VTuber/Open-LLM-VTuber)** ★15k — "Talk to any LLM with hands-free voice interaction." Runs fully offline, Live2D face, voice interruption support, cross-platform. The most popular pick if you want a working local voice+face companion with minimal setup.
- **[Ikaros-521/AI-Vtuber](https://github.com/Ikaros-521/AI-Vtuber)** ★4.6k — Chinese-ecosystem-first virtual broadcaster; huge backend matrix (ChatGPT/Claude/Qwen/local models × Bilibili/Douyin/Kuaishou/YouTube/Twitch/TikTok × edge-tts/VITS/Bert-VITS2/so-vits-svc).
- **[N.E.K.O](https://github.com/Project-N-E-K-O/N.E.K.O)** ★3.2k (formerly Xiao8) — open-source companion agents with realtime voice and vision, long-term memory, Live2D/3D avatars, game-companion modes, and a plugin market; Chinese/English.
- **[LingChat](https://github.com/SlimeBoyOwO/LingChat)** ★2.5k — immersive galgame-style AI chat with emotional expressions, a desktop pet, scheduling, and interactive story modules.
- **[kimjammer/Neuro](https://github.com/kimjammer/Neuro)** ★2.1k — An open-source Neuro-sama recreation, built in seven days as a proof of concept and no longer actively developed; still a good minimal reference for the "AI VTuber that plays games and talks to chat" pattern.
- **[amica](https://github.com/semperai/amica)** ★1.6k — Open-source interface for interactive 3D-character communication with voice synthesis/recognition; simpler and more embeddable than the above.
- **[Soul of Waifu](https://github.com/jofizcd/Soul-of-Waifu)** ★1.5k — Windows desktop app, Live2D/VRM avatars, voice chat, local GGUF model support, plus a full tabletop-RPG mode.
- **[my-neuro](https://github.com/morettt/my-neuro)** ★1.5k — Another personal Neuro-sama-style recreation, actively iterated.
- **[ChatdollKit](https://github.com/uezo/ChatdollKit)** ★1.3k / **[AIAvatarKit](https://github.com/uezo/aiavatarkit)** ★704 — Unity-based SDKs (same author) for turning a 3D model into a conversational agent with voice + facial coordination; good if you want a Unity pipeline rather than web/Electron.
- **[aituber-kit](https://github.com/tegnike/aituber-kit)** ★1.1k — Next.js/TypeScript toolkit for VRM + Live2D + Motion-PNG AI characters with YouTube Live chat ingestion built in; a good "closest stack match" if you're already in the JS/web ecosystem, and usable as a standalone web chat frontend.
- **[ardha27/AI-Waifu-Vtuber](https://github.com/ardha27/AI-Waifu-Vtuber)** ★1.1k — AI streamer stack targeting YouTube/Twitch specifically.
- **[z-waif](https://github.com/SugarcaneDefender/z-waif)** ★609 — "Fully local program to make your own AI waifu." Ties together Oobabooga + RVC + Whisper + VTube Studio + Discord + Minecraft + a custom RAG memory. Explicitly framed as giving you the tools rather than a polished package — see [SugarcaneDefender](#creators--showcases) below for the accompanying tutorials.
- **[AIwaifu (HRNPH)](https://github.com/HRNPH/AIwaifu)** ★518 — Fine-tunable, open-source AI waifu platform explicitly inspired by Neuro-sama.
- Smaller or less active entries in the same genre, worth a look depending on your preferred LLM backend or platform: **[riko_project](https://github.com/rayenfeng/riko_project)** ★1.2k, **[nekro-agent](https://github.com/KroMiose/nekro-agent)** ★1.2k, **[vixevia](https://github.com/IRedDragonICY/vixevia)** ★63, **[Paraworks/BangDreamAi](https://github.com/Paraworks/BangDreamAi)** ★58, **[projectBEA](https://github.com/emqnuele/projectBEA)** ★29.

<sub>[↑ back to top](#table-of-contents)</sub>

---

## Agentic AI Frameworks

General-purpose agent frameworks that aren't companion-specific but are commonly adapted for one — orchestration, tool use, multi-agent coordination.

- **[Model Context Protocol (MCP)](https://modelcontextprotocol.io)** / **[modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers)** ★92k — the open standard for connecting agents to tools and data sources, created by Anthropic and donated in December 2025 to the Linux Foundation's [Agentic AI Foundation](https://aaif.io). Increasingly the default way companion projects expose "hands" (file access, APIs, game controls) to an LLM. See also the [VTube Studio MCP server](https://github.com/hkopenai/vtube-studio-plugin-mcp-server) for a companion-specific example.
- **[OpenClaw](https://github.com/openclaw/openclaw)** ★394k — "Your own personal AI assistant. Any OS. Any Platform." Not companion-specific out of the box, but its scale, cross-platform reach, and general-purpose assistant architecture make it a strong base to reskin into a persistent companion if you'd rather start from a massive, actively-maintained general agent than a waifu-specific project.
- **[Hermes Agent](https://github.com/NousResearch/hermes-agent)** ★263k — "The agent that grows with you," from Nous Research. A self-improving, cross-platform-messaging agent framework; the "grows with you" framing and autonomous skill-creation loop overlap directly with what most companion projects in this list are trying to build from scratch, making it a viable companion foundation on its own.
- **[CrewAI](https://github.com/crewAIInc/crewAI)** ★61k — Role-based multi-agent orchestration; useful if your companion's "mind" is decomposed into cooperating sub-agents (a planner, a memory-writer, a persona-guard, etc.).
- **[LangGraph](https://github.com/langchain-ai/langgraph)** ★45k — Graph-based agent orchestration from the LangChain team; the most common choice for building stateful, branching agent behavior (goal pursuit, multi-step planning) on top of an LLM.
- **[ElizaOS](https://github.com/elizaOS/eliza)** ★20k — "Open source agentic operating system." TypeScript agent framework with a character-JSON persona spec and out-of-box connectors for Discord/Telegram/X/Farcaster/Bluesky/Slack. More general-purpose than waifu-specific, but its character file spec and multi-agent runtime are widely reused (see the [ElizaOS paper](https://arxiv.org/abs/2501.06781)).
- **[Microsoft Agent Framework](https://github.com/microsoft/agent-framework)** ★15k — Microsoft's successor to **[AutoGen](https://github.com/microsoft/autogen)** ★62k, which has been in maintenance mode (bug and security fixes only) since late 2025. AutoGen's multi-agent conversation patterns are still worth studying, but start new work on Agent Framework.
- **[OpenAI Agents SDK](https://github.com/openai/openai-agents-python)** ★31k and **[Claude Agent SDK](https://github.com/anthropics/claude-agent-sdk-python)** ★8.5k — first-party agent-building SDKs from the two largest hosted-model providers; good defaults if you're fine depending on a hosted API rather than local inference.
- **[Pipecat](https://github.com/pipecat-ai/pipecat)** ★17k and **[LiveKit Agents](https://github.com/livekit/agents)** ★15k — real-time voice-agent pipeline frameworks (STT → LLM → TTS orchestration with interruption handling); directly relevant to the voice-loop half of any companion.
- **[Mastra](https://github.com/mastra-ai/mastra)** ★29k, **[Pydantic AI](https://github.com/pydantic/pydantic-ai)** ★21k, **[Strands Agents](https://github.com/strands-agents/harness-sdk)** ★9.2k (AWS) — newer, more typed/structured alternatives to the above; worth watching if you want strong schema guarantees around tool calls.

<sub>[↑ back to top](#table-of-contents)</sub>

---

## Memory & Long-Term Context

The hardest unsolved problem in this space — giving a companion continuity across sessions without an ever-growing, ever-more-expensive context window.

- **[Letta](https://github.com/letta-ai/letta)** ★25k (née **MemGPT**) — the foundational paper/system for OS-style paged memory management in LLM agents ([Packer et al., arXiv:2310.08560](https://arxiv.org/abs/2310.08560)); still the reference architecture most memory systems in this space cite.
- **[Mem0](https://github.com/mem0ai/mem0)** ★69k — "Universal memory layer for AI agents." The most widely adopted drop-in memory layer right now; simple API, good defaults.
- **[Graphiti / Zep](https://github.com/getzep/graphiti)** ★33k — temporally-aware knowledge graphs for agent memory; the state of the art if you need memory that understands *when* a fact was true, not just that it was.
- **[Microsoft GraphRAG](https://github.com/microsoft/graphrag)** ★37k — graph-structured retrieval-augmented generation; a heavier-weight alternative to flat vector RAG for companions with large amounts of lore/history to draw on.
- **Vector stores:** [Qdrant](https://github.com/qdrant/qdrant) ★36k, [Chroma](https://github.com/chroma-core/chroma) ★30k, [pgvector](https://github.com/pgvector/pgvector) ★24k, [Weaviate](https://github.com/weaviate/weaviate) ★17k — the underlying retrieval layer most of the above (or a DIY memory system) sits on top of.
- Related benchmarks worth knowing about when evaluating any of these: **[LongMemEval](https://github.com/xiaowu0162/LongMemEval)** ([arXiv:2410.10813](https://arxiv.org/abs/2410.10813)), **[LoCoMo](https://github.com/snap-research/locomo)**.

<sub>[↑ back to top](#table-of-contents)</sub>

---

## Local LLM Inference & Serving

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** ★134k — the substrate almost everything else in this section is built on; C/C++ LLM inference, runs anywhere from a phone to a server.
- **[Ollama](https://github.com/ollama/ollama)** ★187k — the easiest on-ramp to running local models; most companion projects' "point it at a local model" instructions assume this.
- **[vLLM](https://github.com/vllm-project/vllm)** ★97k and **[SGLang](https://github.com/sgl-project/sglang)** ★39k — high-throughput serving engines, relevant once you're running a companion for more than one user or need low-latency batched inference.
- **[LiteLLM](https://github.com/BerriAI/litellm)** ★63k — a unified API/router across local and hosted LLM providers; the layer that lets a companion swap backends (LM Studio ↔ Ollama ↔ OpenRouter ↔ a hosted API) without touching application code.
- **[oobabooga/textgen](https://github.com/oobabooga/textgen)** ★48k (formerly text-generation-webui) — the long-standing general-purpose local LLM web UI; still the backend of choice for several projects above (z-waif included).
- **[LM Studio](https://lmstudio.ai)** — the most popular local-model GUI/OpenAI-compatible server for non-CLI users.
- **[MLX](https://github.com/ml-explore/mlx)** ★29k / **[mlx-lm](https://github.com/ml-explore/mlx-lm)** (Apple Silicon) and **[TensorRT-LLM](https://github.com/NVIDIA/TensorRT-LLM)** ★15k (NVIDIA) — hardware-specific inference runtimes worth knowing if you're optimizing for a specific machine.

<sub>[↑ back to top](#table-of-contents)</sub>

---

## Open / Roleplay-Tuned Language Models

Base models with strong open weights, plus the community fine-tunes that specifically target character consistency and roleplay over raw benchmark performance. This category turns over faster than any other here — treat named models as starting search terms, not permanent recommendations.

- **Base model families actively used as companion foundations (as of late 2026):** [Qwen 3.x](https://huggingface.co/Qwen) (Alibaba), [Gemma 4](https://huggingface.co/google) (Google), [DeepSeek V4](https://huggingface.co/deepseek-ai), [Mistral Small 4 / Large 4](https://huggingface.co/mistralai), and [Llama 4](https://huggingface.co/meta-llama) (Meta). Pick based on your VRAM budget and licensing needs — and check the license per model, not per family: e.g. Gemma 4 and Qwen3.8-27B are Apache-2.0 and DeepSeek V4.1 is MIT, while Llama 4 and Mistral Large 4 ship under their own custom licenses.
- **Active roleplay/creative-writing fine-tuners:** **[TheDrummer](https://huggingface.co/TheDrummer)** — the most prolific current RP fine-tuner (Behemoth, Artemis, Orion, etc., on recent bases); **[Gryphe](https://huggingface.co/Gryphe)** — the MythoMax author, now publishing Pantheon and StyleTune fine-tunes of Gemma 4 and Qwen. Earlier-generation but still widely referenced: **[Sao10K](https://huggingface.co/Sao10K)** (Euryale, Fimbulvetr) and **[anthracite-org](https://huggingface.co/anthracite-org)** (Magnum).
- **[NousResearch Hermes](https://huggingface.co/NousResearch)** line — strong general instruction-following fine-tunes frequently reused as a roleplay base.
- **Quantized (GGUF) builds** of almost all of the above are published by **[bartowski](https://huggingface.co/bartowski)** and **[mradermacher](https://huggingface.co/mradermacher)** — usually the fastest way to run a new release in llama.cpp/Ollama/LM Studio.
- **Historical favorites** you'll still see in older guides: [MythoMax-L2-13B](https://huggingface.co/Gryphe/MythoMax-L2-13b), [Fimbulvetr-11B-v2](https://huggingface.co/Sao10K/Fimbulvetr-11B-v2), [Psyfighter2](https://huggingface.co/KoboldAI/LLaMA2-13B-Psyfighter2), [Chronos-Hermes-13B](https://huggingface.co/Austism/chronos-hermes-13b-v2) — 2023–24-era Llama-2/Solar fine-tunes, now outclassed by the families above.
- For what's good *this month*, check the current roleplay-model megathread on [r/LocalLLaMA](https://reddit.com/r/LocalLLaMA) or [r/SillyTavernAI](https://reddit.com/r/SillyTavernAI).

<sub>[↑ back to top](#table-of-contents)</sub>

---

## Voice: Text-to-Speech

- **[GPT-SoVITS](https://github.com/RVC-Boss/GPT-SoVITS)** ★65k — few-shot voice cloning with strong quality-per-sample-of-reference-audio; a popular choice specifically for cloning an anime/VTuber-style voice.
- **[Coqui TTS / XTTS-v2](https://github.com/coqui-ai/TTS)** ★46k — the most widely adopted open TTS toolkit; XTTS-v2 specifically is a common default for fast voice cloning from a short sample. The original repo has been unmaintained since Coqui (the company) shut down in early 2024 — use the community-maintained **[idiap/coqui-ai-TTS](https://github.com/idiap/coqui-ai-TTS)** ★2.4k fork for current Python/PyTorch support.
- **[Fish Speech](https://github.com/fishaudio/fish-speech)** ★34k — multilingual zero-shot TTS/voice cloning with strong expressiveness; one of the most popular newer open TTS projects.
- **[Kokoro-82M](https://huggingface.co/hexgrad/Kokoro-82M)** ([repo](https://github.com/hexgrad/kokoro) ★10k) — small (82M param), fast, Apache-2.0 TTS model; a common default for local-first, CPU-friendly companion voices (used by YuriOS, among others).
- **[Resemble Chatterbox](https://github.com/resemble-ai/chatterbox)** ★28k — open TTS with zero-shot cloning and an emotion-exaggeration control, useful for giving a character a recognizable emotional range.
- **[IndexTTS](https://github.com/index-tts/index-tts)** ★25k — controllable zero-shot TTS with fine-grained duration and emotion control.
- **[CosyVoice](https://github.com/QwenAudio/CosyVoice)** ★24k — multilingual voice generation with full inference/training/deployment tooling.
- **[F5-TTS](https://github.com/SWivid/F5-TTS)** ★16k — flow-matching zero-shot TTS; fast and natural-sounding cloning from a short reference clip.
- **[Sesame CSM](https://github.com/SesameAILabs/csm)** ★15k ([weights](https://huggingface.co/sesame/csm-1b)) — a conversational speech model that conditions on dialogue context, so prosody follows the flow of the conversation rather than each line in isolation.
- **[RVC (Retrieval-based Voice Conversion)](https://github.com/RVC-Project/Retrieval-based-Voice-Conversion-WebUI)** ★39k — real-time-capable voice conversion; "train a good VC model with ≤10 min of data." Frequently paired with a separate TTS engine as a voice-conversion pass.
- **Older but still used:** [Bark](https://github.com/suno-ai/bark) ★39k (expressive — laughs, sighs, tone — but heavy and hard to control), [OpenVoice](https://github.com/myshell-ai/OpenVoice) ★38k, [MeloTTS](https://github.com/myshell-ai/MeloTTS) ★7.7k, [StyleTTS2](https://github.com/yl4579/StyleTTS2) ★6.4k, [Orpheus](https://huggingface.co/canopylabs/orpheus-3b-0.1-ft). Bark, MeloTTS and StyleTTS2 haven't been updated since 2024.

<sub>[↑ back to top](#table-of-contents)</sub>

---

## Voice: Speech-to-Text & Turn-Taking

- **[Whisper](https://github.com/openai/whisper)** ★113k / **[faster-whisper](https://github.com/SYSTRAN/faster-whisper)** ★27k — the default open STT stack; faster-whisper (CTranslate2-backed) is what most real-time companion projects actually deploy for latency reasons.
- **[Silero VAD](https://github.com/snakers4/silero-vad)** ★11k — the standard lightweight voice-activity-detector for deciding when the user has actually stopped talking; load-bearing for any "hands-free" voice loop.
- **[RealtimeSTT](https://github.com/KoljaB/RealtimeSTT)** ★10k / **[RealtimeTTS](https://github.com/KoljaB/RealtimeTTS)** ★4.1k (same author) — streaming wrappers with built-in VAD and wake-word support that specifically target low first-byte latency for conversational use.
- **[Moshi](https://github.com/kyutai-labs/moshi)** ★11k (Kyutai) — a full-duplex speech-text model that listens and speaks at the same time, so it can handle interruptions and backchannels without a separate turn-taking layer. Kyutai's **[Unmute](https://github.com/kyutai-labs/unmute)** ★1.5k applies their streaming STT/TTS around any text LLM instead.
- NVIDIA **[Parakeet](https://huggingface.co/nvidia/parakeet-tdt-0.6b-v3)** / **[Canary](https://huggingface.co/nvidia/canary-1b-flash)** — very fast open STT models worth benchmarking against faster-whisper if latency is your bottleneck.

<sub>[↑ back to top](#table-of-contents)</sub>

---

## Embodiment: Avatars, VTubing & Motion

- **[VTube Studio](https://store.steampowered.com/app/1325860/VTube_Studio/)** + its **[public API](https://github.com/DenchiSoft/VTubeStudio)** ★1.3k — the dominant Live2D tracking/animation app; nearly every project above that has a 2D face drives it through this API (see [VTubeStudioJS](https://github.com/Hawkbat/VTubeStudioJS) and the [VTube Studio MCP server](https://github.com/hkopenai/vtube-studio-plugin-mcp-server) for programmatic control).
- **[VMC Protocol](https://protocol.vmc.info/)** ([sh-akira/VirtualMotionCapture](https://github.com/sh-akira/VirtualMotionCapture) ★828) — MIT-licensed OSC-over-UDP protocol for streaming avatar motion between apps; the closest thing this space has to a universal wire format. Senders include VSeeFace/Waidayo/MocapForAll; receivers include Warudo/VNyan/EVMC4U/three-vrm.
- **[three-vrm](https://github.com/pixiv/three-vrm)** ★2.3k + **[VRM specification](https://github.com/vrm-c/vrm-specification)** — the standard 3D humanoid avatar format for web/three.js-based companions, plus its Unity counterpart **[UniVRM](https://github.com/vrm-c/UniVRM)** ★3.4k.
- **[VRoid Studio](https://vroid.com/en/studio)** / **[VRoid Hub](https://hub.vroid.com)** — the easiest free tool for making (and sharing) your own VRM avatar without 3D modeling skills.
- **[Live2D Cubism](https://www.live2d.com/en/)** (Editor + SDK) — the de facto standard 2D "paper puppet" animation format for VTuber-style faces. Proprietary: the Editor has a free tier and a paid Pro license, and the SDK is free for individuals and small businesses, with a paid license above a revenue threshold.
- **[Warudo](https://warudo.app)**, **[VNyan](https://suvidriel.itch.io/vnyan)**, **[VSeeFace](https://www.vseeface.icu)** — VRM/3D avatar rigs and streaming tools, each supporting VMC-protocol input from a companion backend.
- **[CharacterStudio](https://github.com/M3-org/CharacterStudio)** ★379 — open-source VRM avatar creation/customization tool.
- **[vrm-samples](https://github.com/madjin/vrm-samples)** ★97 — a collection of openly-licensed VRM avatar models to start from instead of commissioning one (not updated since 2022, but the models still work).
- **[ARKit blendshapes](https://developer.apple.com/documentation/arkit/arfaceanchor/blendshapelocation)** (52-shape standard) — the de facto facial-expression interchange format if you're doing camera-based face tracking (iPhone or otherwise) to drive an avatar.
- **Lip-sync & face animation** (for photo/illustration-based characters rather than rigged avatars):
  - **[LivePortrait](https://github.com/KlingAIResearch/LivePortrait)** ★19k — animates a single portrait image from a driving video or expression parameters; a cheap way to give a static character illustration a moving face.
  - **[MuseTalk](https://github.com/TMElyralab/MuseTalk)** ★6.9k — real-time, high-quality lip-sync for driving a face from your companion's TTS audio.

<sub>[↑ back to top](#table-of-contents)</sub>

---

## Image & Video Generation

Useful for character art, expression sheets, promotional material, or dynamically generated scenes.

- **[ComfyUI](https://github.com/Comfy-Org/ComfyUI)** ★146k — node-based workflow tool; the most flexible and now the de facto standard for anyone doing non-trivial image/video-gen pipelines (LoRA stacking, ControlNet, batch expression generation).
- **[AUTOMATIC1111 / stable-diffusion-webui](https://github.com/AUTOMATIC1111/stable-diffusion-webui)** ★165k — the original simple web UI for Stable Diffusion and still the most-documented, but its main branch hasn't had a commit since 2024. New users wanting the same interface should use **[Forge](https://github.com/lllyasviel/stable-diffusion-webui-forge)** ★13k (faster, lower VRAM; its own development slowed in 2025) or the actively maintained **[reForge](https://github.com/Panchovix/stable-diffusion-webui-reForge)** ★1k.
- **[InvokeAI](https://github.com/invoke-ai/InvokeAI)** ★29k — polished, canvas-centric creative UI; a good middle ground between A1111-style simplicity and ComfyUI's power.
- **[SwarmUI](https://github.com/mcmonkeyprojects/SwarmUI)** ★4.8k — a friendlier front end that runs ComfyUI as its backend, so you can drop into the node graph when you need to.
- **[Fooocus](https://github.com/lllyasviel/Fooocus)** ★54k — "focus on prompting," a much simpler SDXL UI; now in limited long-term support (bug fixes only), so fine to use but don't expect new model support.
- **Model families:** SDXL, Flux, and SD3 (open-weight, compatible with all the UIs above).
- **Anime-style checkpoints:** **[Illustrious XL](https://huggingface.co/OnomaAIResearch/Illustrious-xl-early-release-v0)**, **[NoobAI-XL](https://huggingface.co/Laxhar/noobai-XL-1.1)**, **[Pony Diffusion V6 XL](https://civitai.com/models/257749/pony-diffusion-v6-xl)**, and **[Animagine XL 4.0](https://huggingface.co/cagliostrolab/animagine-xl-4.0)** — the SDXL-based anime lineages that most current character LoRAs target. The older SD1.5-era anime models largely descend from the leaked NovelAI checkpoint (see [Adjacent Reading](#adjacent-reading-not-strictly-open-source)).
- **[Civitai](https://civitai.com)** — the primary source and community hub for downloading all of the above: base models, character/style LoRAs, embeddings, and ControlNet/VAE add-ons.
- **Video generation:** **[Wan 2.2](https://github.com/Wan-Video/Wan2.2)** ★19k (Alibaba), **[HunyuanVideo](https://github.com/Tencent-Hunyuan/HunyuanVideo)** ★13k (Tencent), and **[LTX-Video](https://github.com/Lightricks/LTX-Video)** ★11k / **[LTX-2](https://github.com/Lightricks/LTX-2)** ★10k (Lightricks; LTX-2 generates synchronized audio and video) — open-weight text/image-to-video models for animated character clips, mostly run through ComfyUI.

<sub>[↑ back to top](#table-of-contents)</sub>

---

## Character Formats & Persona Standards

- **[Character Card Spec V3](https://github.com/kwaroran/character-card-spec-v3)** — the current character-card interchange standard; supersedes V2.
- **[Character Card Spec V2](https://github.com/malfoyslastname/character-card-spec-v2)** — still widely supported for backward compatibility across frontends.
- **[SillyTavern World Info docs](https://docs.sillytavern.app/usage/core-concepts/worldinfo/)** — the reference explanation of lorebook/world-info mechanics (keyword-triggered context injection), which most companion memory systems reinvent in some form.

<sub>[↑ back to top](#table-of-contents)</sub>

---

## Character Card Explorers & Repositories

Sites for browsing and downloading ready-made character cards (PNG/JSON, V2/V3 spec) that drop straight into SillyTavern or any compatible frontend.

- **[Chub.ai / CharacterHub](https://chub.ai)** — the largest and most actively moderated card repository, with V2/V3 filtering and an active creator community.
- **[AICharacterCards.com](https://aicharactercards.com)** — a large curated V2/V3 card library.
- **[CharaVault](https://charavault.net)** — a 195k+ card preservation archive with direct PNG/JSON downloads, moderated uploads, and a public API.
- **[RisuRealm](https://realm.risuai.net)** — the card-sharing hub for RisuAI; supports V2, V3, and CHARX card downloads alongside lorebooks and presets.
- **[Pygmalion.chat](https://pygmalion.chat)** — PygmalionAI's own card library; cards are explicitly designed to import/export without lock-in.
- **[Datacat](https://datacat.run/characters/recent)** — a tag-browsable index of public character cards.
- **[JanitorAI](https://janitorai.com)** — a huge closed roleplay platform with an enormous card catalog; it has no native export button, so pulling a SillyTavern-compatible PNG requires a third-party tool like [jai-card-extractor](https://github.com/erpocalypse/jai-card-extractor) or a similar userscript/extension.

<sub>[↑ back to top](#table-of-contents)</sub>

---

## Frontends & Chat Clients

- **[SillyTavern](https://github.com/SillyTavern/SillyTavern)** ★36k — the dominant self-hosted LLM roleplay frontend. Not a "waifu app" per se, but most character-card/lorebook-based companions in this list are built on top of it or compatible with it (see [Character Formats](#character-formats--persona-standards)). Large extension ecosystem — see [SillyTavern-CharacterLibrary](https://github.com/Sillyanonymous/SillyTavern-CharacterLibrary) as one example.
- **[Open WebUI](https://github.com/open-webui/open-webui)** ★158k — general-purpose self-hosted LLM chat UI; less roleplay-specialized than SillyTavern but a clean base if you're building your own layer on top.
- Several [Full-Stack projects](#full-stack-ai-companion--ai-vtuber-projects) — notably aituber-kit and amica — also work as standalone web chat frontends.

<sub>[↑ back to top](#table-of-contents)</sub>

---

## Fine-Tuning, Datasets & Synthetic Data

If prompting and RAG aren't getting your companion's voice consistent enough, this is the next rung up.

- **[LlamaFactory](https://github.com/hiyouga/LlamaFactory)** ★76k and **[Axolotl](https://github.com/axolotl-ai-cloud/axolotl)** ★13k — the two most popular open fine-tuning frameworks (LoRA/QLoRA/full fine-tune) for adapting a base model to a specific character voice.
- **[distilabel](https://github.com/argilla-io/distilabel)** ★3.5k and **[synthetic-data-generator](https://github.com/argilla-io/synthetic-data-generator)** ★590 (Argilla) — pipelines for generating synthetic training/preference data, relevant if you're building an SFT/DPO dataset from your companion's own conversation logs.
- **[Magpie](https://github.com/magpie-align/magpie)** ★902 — a method for generating high-quality instruction data directly from an aligned model, no seed prompts needed.
- **Companion-relevant datasets on Hugging Face:** [PygmalionAI/PIPPA](https://huggingface.co/datasets/PygmalionAI/PIPPA) (roleplay conversation corpus), [lemonilia/LimaRP](https://huggingface.co/datasets/lemonilia/LimaRP), [taozi555/rp-opus](https://huggingface.co/datasets/taozi555/rp-opus).
- **[mlabonne/llm-datasets](https://github.com/mlabonne/llm-datasets)** ★4.8k and **[awesome-instruction-datasets](https://github.com/jianzhnie/awesome-instruction-datasets)** ★753 — curated indexes of instruction/fine-tuning datasets more broadly.
- **[Lorebooks as active scenario/character guidance](https://huggingface.co/sphiratrioth666/Lorebooks_as_ACTIVE_scenario_and_character_guidance_tool)** — a widely-referenced practical guide to using SillyTavern-style lorebooks as a cheaper alternative to fine-tuning.

<sub>[↑ back to top](#table-of-contents)</sub>

---

## Papers, Guides & Reading

- **[Anthropic — "Building Effective Agents"](https://www.anthropic.com/research/building-effective-agents)** and **["Introducing MCP"](https://www.anthropic.com/news/model-context-protocol)** — the most-cited practical framing for agent architecture generally.
- **MemGPT** — Packer et al., [arXiv:2310.08560](https://arxiv.org/abs/2310.08560) — foundational memory-management paper (became Letta).
- **"Lost in the Middle"** — Liu et al., 2023, [arXiv:2307.03172](https://arxiv.org/abs/2307.03172) — why naively stuffing context windows degrades recall; motivates most memory-retrieval design in this space.
- **ReAct** — Yao et al., 2023, [arXiv:2210.03629](https://arxiv.org/abs/2210.03629) — the reasoning+acting pattern nearly all tool-using agents implement in some form.
- **"Eliza: A Web3-friendly AI Agent Operating System"** — [arXiv:2501.06781](https://arxiv.org/abs/2501.06781) — the ElizaOS paper.
- **Foundational ML papers worth knowing if you're going past prompting into fine-tuning:** [Attention Is All You Need](https://arxiv.org/abs/1706.03762), [Chinchilla](https://arxiv.org/abs/2203.15556) (compute-optimal scaling), [LoRA](https://arxiv.org/abs/2106.09685), [QLoRA](https://arxiv.org/abs/2305.14314), [DPO](https://arxiv.org/abs/2305.18290), [KTO](https://arxiv.org/abs/2402.01306), [ORPO](https://arxiv.org/abs/2403.07691), [InstructGPT/RLHF](https://arxiv.org/abs/2203.02155).
- **[PayDevs/awesome-oss-monetization](https://github.com/PayDevs/awesome-oss-monetization)** ★934 — not companion-specific, but relevant if you intend to ship any of this as a product.
- **[The Agentic Waifu Codex](#yurios--my-project)** — see above; its Appendix C reading list and Appendix B tools/stacks table are the direct source for a large share of this document.

<sub>[↑ back to top](#table-of-contents)</sub>

---

## Communities & Websites

- **[r/LocalLLaMA](https://reddit.com/r/LocalLLaMA)** — the center of gravity for local-model discussion generally; essential even though not companion-specific.
- **[SillyTavern Discord](https://discord.gg/sillytavern)** and **[r/SillyTavernAI](https://reddit.com/r/SillyTavernAI)** — the largest roleplay-frontend community; most practical "how do I actually get good outputs" knowledge lives here.
- **[r/MyBoyfriendIsAI](https://reddit.com/r/MyBoyfriendIsAI)**, r/AICompanions, r/AIRomance — user-side (not developer-side) communities discussing the companion-relationship experience itself; valuable if you want to understand what people actually want from these products, as distinct from what's technically interesting to build.
- **[r/VirtualYoutubers](https://reddit.com/r/VirtualYoutubers)**, r/AIVtuber — VTuber-culture-side communities, useful for the embodiment/streaming half of this space.
- **[VRoid Hub](https://hub.vroid.com)** / Pixiv VRM communities and the **[VRChat](https://hello.vrchat.com)** community — avatar-asset and 3D-embodiment communities.
- **[Hugging Face forums](https://discuss.huggingface.co)** — model- and dataset-specific discussion.
- Model and card hubs with active communities of their own — [Civitai](#image--video-generation), [Chub.ai](#character-card-explorers--repositories) and the other card sites — are covered in their respective sections above.
- *(Deliberately not linked as chat platforms: Character.AI, Replika, Kindroid, and similar closed products — mentioned only where relevant as points of comparison, since this list's focus is open, self-hostable tooling. JanitorAI is the exception, linked above solely as a card source.)*

<sub>[↑ back to top](#table-of-contents)</sub>

---

## Creators & Showcases

Not open source, but essential context — this is the "why" behind most of the projects above, plus the people documenting how to build them.

- **[Neuro-sama](https://www.youtube.com/@Neurosama)** (created and operated by **Vedal**, [@vedal987](https://www.youtube.com/user/Vedal987)) — the AI VTuber that essentially created this genre: an LLM-driven virtual streamer that plays games (osu!, Minecraft, Pokémon), sings, and banters live with chat, live since December 2022. Fully closed/proprietary, but the reference point nearly every project above (AIRI, kimjammer/Neuro, my-neuro, AIwaifu) explicitly cites as what they're trying to recreate in the open. Essential viewing for what the finished product looks like at the top of the field.
- **[SugarcaneDefender](https://www.youtube.com/@SugarcaneDefender)** — creator of [z-waif](https://github.com/SugarcaneDefender/z-waif); build/install/tutorial videos for assembling a fully local AI waifu (Oobabooga + RVC + Whisper + VTube Studio). One of the few channels documenting the DIY local-companion build process end to end rather than reviewing closed apps.
- **[AIRI project DevLogs](https://airi.moeru.ai/docs/en/blog/)** — the closest thing to a running build-log for the most important open project in this space.
- *For current build-along videos, search YouTube for "AI VTuber tutorial," "Open-LLM-VTuber setup," or "local AI waifu Live2D" — this corner of YouTube turns over quickly, so a live search usually beats a static link list.*

<sub>[↑ back to top](#table-of-contents)</sub>

---

## Adjacent Reading (not strictly open source)

Proprietary products/platforms mentioned only because they've published something genuinely educational or field-defining. (Replika, the most-studied case of long-term AI relationships, has published no developer material worth linking.)

- **[Character.AI — "Optimizing AI Inference at Character.AI"](https://research.character.ai/optimizing-inference/)** (2024) — how the largest closed companion platform serves very long chat histories cheaply (multi-query attention, cross-layer KV-cache sharing, int8 training). Directly relevant if you're running a companion whose conversations never end.
- **NovelAI** — proprietary, but its anime-style Stable Diffusion checkpoints are the historical ancestor of most SD1.5-era open anime models, and it open-sourced the **[aspect-ratio bucketing](https://github.com/NovelAI/novelai-aspect-ratio-bucketing)** training technique now used across the fine-tuning ecosystem.

<sub>[↑ back to top](#table-of-contents)</sub>

---

## AI-Waifu-Adjacent Media: Anime, TV, Film & Books

The cultural DNA this whole field is downstream of, for when you want to think about the *idea* of an AI companion rather than the implementation.

**Anime & Manga**
- *Chobits* (CLAMP) — the foundational "persocom" text for this entire genre; still the most direct fictional analogue to a physically-embodied personal AI companion.
- *Time of Eve* (Yasuhiro Yoshiura) — android companions and the ethics of treating them as people; probably the single best short work to watch before designing a companion's personality.
- *Ghost in the Shell* (Masamune Shirow / Mamoru Oshii) — foundational for thinking about mind/memory/identity as software, directly upstream of how this list's "memory" section frames things.
- *Plastic Memories* — mortality and memory in android companions; emotionally brutal, relevant to anyone building "the companion remembers you" features.
- *Vivy: Fluorite Eye's Song* — an AI singer drawn into a century-long mission to stop a war between AIs and humans; close in theme to the "agentic" framing of this list.
- *Beatless* (Satoshi Hase) — humanoid "hIE" androids and a boy who chooses to trust one; centrally about whether an AI companion's apparent heart matters if you can't verify it.
- *ATRI -My Dear Moments-* — a robot girl salvaged from the sea and the boy she decides to serve; a gentle, direct take on the companion-who-learns-to-be-human story.
- *Sword Art Online: Alicization* arc — AI/digital-consciousness companion tropes, more pulp than the above but influential on the community's imagination.

**Film & TV**
- *Her* (2013) — the reference point everyone in this space eventually gets compared to; a genuinely good design document disguised as a movie.
- *Ex Machina* (2014) — the counterpoint to *Her*; agency, deception, and what it means for a companion to have its own goals.
- *Klara and the Sun* (2026, dir. Taika Waititi; based on the Kazuo Ishiguro novel below) — an android companion story about devotion and the limits of care.
- *Westworld* (HBO) — long-run exploration of embodied AI, memory-editing, and autonomy at a much larger scale.
- *Black Mirror* — several standalone episodes ("Be Right Back," "San Junipero," "Rachel, Jack and Ashley Too") are directly about AI/digital companionship and consequence.

**Books**
- *Klara and the Sun* — Kazuo Ishiguro. A solar-powered android companion narrates her own purchase and purpose; the best-written recent treatment of devotion-as-design in an artificial mind.
- *Do Androids Dream of Electric Sheep?* — Philip K. Dick. The foundational text for "how do you tell a person from a companion," underlying nearly everything downstream including *Blade Runner*.
- *Machines Like Me* — Ian McEwan. A domestic android-companion story explicitly about the ethics of building something that can suffer.
- *I Have No Mouth, and I Must Scream* — Harlan Ellison (1967 short story). Not about companions, but the essential "what if the mind you built resents you" text.

---

*Corrections, additions, and disagreements welcome. If you maintain a project listed here and think its placement or description is wrong, [open an issue](https://github.com/yuri-os/awesome-agentic-ai-waifus/issues/new/choose) — see [CONTRIBUTING.md](CONTRIBUTING.md).*
