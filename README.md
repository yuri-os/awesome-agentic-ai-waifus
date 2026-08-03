# Awesome Agentic AI Waifus & Companions

> A one-stop, opinionated map of the open-source AI companion / "agentic waifu" ecosystem — frameworks, full-stack projects, models, embodiment tech, communities, people, and the media that inspired all of it.

This list focuses on **open source** and **freely available** projects, papers, and guides for building agentic AI companions — local-first chatbots-with-a-body that remember you, look like something, sound like something, and (increasingly) act on their own initiative. It deliberately avoids listing closed, proprietary companion apps (Character.AI, Replika, Kindroid, etc.) except where they've published genuinely useful research, specs, or educational material. See [Adjacent Reading](#adjacent-reading--not-strictly-open-source) for the few exceptions.

Within each section, entries are roughly ordered by **importance/maturity** (GitHub stars, ecosystem centrality, how load-bearing the project is), not alphabetically — the thing you should look at first is at the top.

**Disclosure of bias:** I am the author of [**YuriOS**](#yurios--my-project) and the accompanying book [**The Agentic Waifu Codex**](#yurios--my-project), which are included below in their own clearly-marked section. I've tried to be honest about where they sit relative to the rest of the field rather than overselling them — judge for yourself.

Contributions/corrections welcome — this is a living document.

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
- [Other Awesome Lists](#other-awesome-lists)
- [Communities & Websites](#communities--websites)
- [Notable AI VTubers / Streamers](#notable-ai-vtubers--streamers)
- [YouTube Channels](#youtube-channels)
- [Adjacent Reading (not strictly open source)](#adjacent-reading--not-strictly-open-source)
- [AI-Waifu-Adjacent Media: Anime, TV, Film & Books](#ai-waifu-adjacent-media-anime-tv-film--books)

---

## Prior Art (the lists this one stands on)

This list exists in a small genre. Read these too — they overlap with this one but each has a different center of gravity.

- **[proj-airi/awesome-ai-vtubers](https://github.com/proj-airi/awesome-ai-vtubers)** — the densest single catalog of AI VTuber codebases (streaming-first: Bilibili/Twitch/YouTube integration, Live2D). Maintained by the team behind AIRI.
- **[parallelarc/Awesome-AI-Waifu](https://github.com/parallelarc/Awesome-AI-Waifu)** — companion-first rather than streaming-first; good frameworks/infrastructure split.
- **[PayDevs/awesome-oss-monetization](https://github.com/PayDevs/awesome-oss-monetization)** — not companion-specific, but relevant if you intend to ship any of this as a product.

---

## YuriOS — My Project

*(Flagged up front per the disclosure above — take the framing with a grain of salt, but the code and book are real and free.)*

- **[YuriOS](https://github.com/yuri-os/YuriOS)** ([yurios.org](https://yurios.org)) — An always-on, local-first, Apache-2.0 AI companion runtime. What differentiates it from most projects in [Full-Stack Projects](#full-stack-ai-companion--ai-vtuber-projects) below is the **mind**: a continuously running cognitive tick loop (sense → appraise → decide → act → reflect → regulate) that gives the companion its own goals, consolidates memory overnight ("dreaming"), tracks promises it's made to you, edits its own persona over time, and decides — under a conservative two-gate salience model — when it's allowed to proactively message you, rather than only ever responding when spoken to. Body is VRM (three.js/three-vrm) or Live2D; voice loop is faster-whisper + Kokoro-82M/GPT-SoVITS + silero-vad; everything the companion knows about you and itself is stored as plain markdown in a git-backed "Vault" on your own disk. No account, no telemetry, works with any LLM backend via LiteLLM (LM Studio, Ollama, OpenRouter, hosted APIs) — a local GPU is only required if you run the models locally; point it at OpenRouter or another hosted API and it runs fine without one. 225-test suite; the test suite itself runs offline/no-GPU, using fakes in place of every heavy backend.
- **[The Agentic Waifu Codex](https://yurios.org/book/)** (aka *Building Agentic Waifus*) — a free, 465-page, 45-chapter practitioner's book: character design and lore, memory/RAG/agentic architecture, voice and avatar embodiment, five runnable reference implementations that build up to YuriOS itself, and the creator-economy/monetization side most technical guides skip. [PDF releases](https://github.com/yuri-os/AgenticWaifuCodex/releases/latest) · [source](https://github.com/yuri-os/AgenticWaifuCodex). Its appendices (tools/stacks, reading list, communities) fed directly into this list — if you want the long-form version of this document's reasoning, that's where it lives.

Where YuriOS sits relative to its nearest neighbors, honestly: **[AIRI](https://github.com/moeru-ai/airi)** has a much bigger community, ships further along the streaming/gaming axis (Minecraft, Factorio), and is the more mature *product*. **[z-waif](https://github.com/SugarcaneDefender/z-waif)** and **[Soul of Waifu](https://github.com/jofizcd/Soul-of-Waifu)** are more turnkey if you just want a working local waifu today. YuriOS's bet is narrower and specifically about the always-on autonomy/mind loop — if that's not what you're after, one of those three is probably the better starting point.

---

## Full-Stack AI Companion / AI VTuber Projects

Complete, runnable companion/VTuber applications — pick one of these if you want something working end-to-end rather than assembling a stack yourself.

- **[AIRI](https://github.com/moeru-ai/airi)** ★43k — "A container of souls of AI waifu." Self-hosted, cross-platform (Web/macOS/Windows) companion with realtime voice chat and the ability to actually play games (Minecraft, Factorio). The most complete and actively developed project in this space; explicitly aimed at "Neuro-sama's altitude." Best single reference implementation to study.
- **[Open-LLM-VTuber](https://github.com/Open-LLM-VTuber/Open-LLM-VTuber)** ★12.8k — "Talk to any LLM with hands-free voice interaction." Runs fully offline, Live2D face, voice interruption support, cross-platform. The most popular pick if you want a working local voice+face companion with minimal setup.
- **[SillyTavern](https://github.com/SillyTavern/SillyTavern)** ★31k — Not a "waifu app" per se but the dominant open-source LLM roleplay frontend; most character-card/lorebook-based companions in this list are built on top of it or compatible with it. See also [Character Formats](#character-formats--persona-standards).
- **[ElizaOS](https://github.com/elizaOS/eliza)** ★18.8k — "Open source agentic operating system." TypeScript agent framework with a character-JSON persona spec and out-of-box connectors for Discord/Telegram/X/Farcaster/Bluesky/Slack. More general-purpose agent framework than waifu-specific, but its character file spec and multi-agent runtime are widely reused (see [Building Effective Agents](#papers-guides--reading) research on it).
- **[Ikaros-521/AI-Vtuber](https://github.com/Ikaros-521/AI-Vtuber)** ★4.4k — Chinese-ecosystem-first virtual broadcaster; huge backend matrix (ChatGPT/Claude/Qwen/local models × Bilibili/Douyin/Kuaishou/YouTube/Twitch/TikTok × edge-tts/VITS/Bert-VITS2/so-vits-svc).
- **[z-waif](https://github.com/SugarcaneDefender/z-waif)** ★550 — "Fully local program to make your own AI waifu." Ties together Oobabooga + RVC + Whisper + VTube Studio + Discord + Minecraft + a custom RAG memory. Explicitly framed as giving you the tools rather than a polished package — see [SugarcaneDefender](#youtube-channels) below for the accompanying tutorials.
- **[Soul of Waifu](https://github.com/jofizcd/Soul-of-Waifu)** ★866 — Windows desktop app, Live2D/VRM avatars, voice chat, local GGUF model support, plus a full tabletop-RPG mode.
- **[kimjammer/Neuro](https://github.com/kimjammer/Neuro)** ★2k — An open-source Neuro-sama recreation, built in seven days as a proof of concept; good minimal reference for the "AI VTuber that plays games and talks to chat" pattern.
- **[my-neuro](https://github.com/morettt/my-neuro)** — Another personal Neuro-sama-style recreation, actively iterated.
- **[AIwaifu (HRNPH)](https://github.com/HRNPH/AIwaifu)** ★507 — Fine-tunable, open-source AI waifu platform explicitly inspired by Neuro-sama.
- **[ardha27/AI-Waifu-Vtuber](https://github.com/ardha27/AI-Waifu-Vtuber)** ★1.1k — AI streamer stack targeting YouTube/Twitch specifically.
- **[amica](https://github.com/semperai/amica)** ★1.6k — Open-source interface for interactive 3D-character communication with voice synthesis/recognition; simpler and more embeddable than the above.
- **[aituber-kit](https://github.com/tegnike/aituber-kit)** ★1k — Next.js/TypeScript toolkit for VRM + Live2D + Motion-PNG AI characters with YouTube Live chat ingestion built in; a good "closest stack match" if you're already in the JS/web ecosystem.
- **[ChatdollKit](https://github.com/uezo/ChatdollKit)** ★1.2k / **[AIAvatarKit](https://github.com/uezo/aiavatarkit)** ★647 — Unity-based SDKs (same author) for turning a 3D model into a conversational agent with voice + facial coordination; good if you want a Unity pipeline rather than web/Electron.
- **[Paraworks/BangDreamAi](https://github.com/Paraworks/BangDreamAi)**, **[projectBEA](https://github.com/emqnuele/projectBEA)**, **[riko_project](https://github.com/rayenfeng/riko_project)**, **[LingChat](https://github.com/SlimeBoyOwO/LingChat)**, **[N.E.K.O](https://github.com/Project-N-E-K-O/N.E.K.O)** (formerly Xiao8), **[vixevia](https://github.com/IRedDragonICY/vixevia)**, **[nekro-agent](https://github.com/KroMiose/nekro-agent)** — smaller/newer entries in the same genre, worth a look depending on your preferred LLM backend or platform.

---

## Agentic AI Frameworks

General-purpose agent frameworks that aren't companion-specific but are commonly adapted for one — orchestration, tool use, multi-agent coordination.

- **[Model Context Protocol (MCP)](https://modelcontextprotocol.io)** / **[modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers)** ★89k — Anthropic's open standard for connecting agents to tools and data sources. Increasingly the default way companion projects expose "hands" (file access, APIs, game controls) to an LLM. See also the [VTube Studio MCP server](https://github.com/hkopenai/vtube-studio-plugin-mcp-server) for a companion-specific example.
- **[OpenClaw](https://github.com/openclaw/openclaw)** ★384k — "Your own personal AI assistant. Any OS. Any Platform." Not companion-specific out of the box, but its scale, cross-platform reach, and general-purpose assistant architecture make it a strong base to reskin into a persistent companion if you'd rather start from a massive, actively-maintained general agent than a waifu-specific project.
- **[Hermes Agent](https://github.com/NousResearch/hermes-agent)** ★221k — "The agent that grows with you," from Nous Research. A self-improving, cross-platform-messaging agent framework; the "grows with you" framing and autonomous skill-creation loop overlap directly with what most companion projects in this list are trying to build from scratch, making it a viable companion foundation on its own.
- **[LangGraph](https://github.com/langchain-ai/langgraph)** ★38k — Graph-based agent orchestration from the LangChain team; the most common choice for building stateful, branching agent behavior (goal pursuit, multi-step planning) on top of an LLM.
- **[CrewAI](https://github.com/crewAIInc/crewAI)** ★56k — Role-based multi-agent orchestration; useful if your companion's "mind" is decomposed into cooperating sub-agents (a planner, a memory-writer, a persona-guard, etc.).
- **[Microsoft AutoGen](https://github.com/microsoft/autogen)** ★60k — Programming framework for agentic AI with strong multi-agent conversation patterns.
- **[ElizaOS](https://github.com/elizaOS/eliza)** ★18.8k — see above; notable here as a full character-based agent OS rather than just an orchestration library.
- **Claude Agent SDK** and **OpenAI Agents SDK** — first-party agent-building SDKs from the two largest hosted-model providers; good defaults if you're fine depending on a hosted API rather than local inference.
- **[Pipecat](https://github.com/pipecat-ai/pipecat)** and **LiveKit Agents** — real-time voice-agent pipeline frameworks (STT → LLM → TTS orchestration with interruption handling); directly relevant to the voice-loop half of any companion.
- **Pydantic AI**, **Mastra**, **Strands Agents (AWS)** — newer, more typed/structured alternatives to the above; worth watching if you want strong schema guarantees around tool calls.

---

## Memory & Long-Term Context

The hardest unsolved problem in this space — giving a companion continuity across sessions without an ever-growing, ever-more-expensive context window.

- **[Letta](https://github.com/letta-ai/letta)** ★24k (née **MemGPT**) — the foundational paper/system for OS-style paged memory management in LLM agents ([Packer et al., arXiv:2310.08560](https://arxiv.org/abs/2310.08560)); still the reference architecture most memory systems in this space cite.
- **[Mem0](https://github.com/mem0ai/mem0)** ★62k — "Universal memory layer for AI agents." The most widely adopted drop-in memory layer right now; simple API, good defaults.
- **[Graphiti / Zep](https://github.com/getzep/graphiti)** ★29k — temporally-aware knowledge graphs for agent memory; the state of the art if you need memory that understands *when* a fact was true, not just that it was.
- **[Microsoft GraphRAG](https://github.com/microsoft/graphrag)** — graph-structured retrieval-augmented generation; a heavier-weight alternative to flat vector RAG for companions with large amounts of lore/history to draw on.
- **Vector stores:** [Qdrant](https://github.com/qdrant/qdrant), [Chroma](https://github.com/chroma-core/chroma), [Weaviate](https://github.com/weaviate/weaviate), [pgvector](https://github.com/pgvector/pgvector) — the underlying retrieval layer most of the above (or a DIY memory system) sits on top of.
- Related benchmarks worth knowing about when evaluating any of these: **LongMemEval**, **LoCoMo**.

---

## Local LLM Inference & Serving

- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — the substrate almost everything else in this section is built on; C/C++ LLM inference, runs anywhere from a phone to a server.
- **[Ollama](https://github.com/ollama/ollama)** ★177k — the easiest on-ramp to running local models; most companion projects' "point it at a local model" instructions assume this.
- **[oobabooga/text-generation-webui](https://github.com/oobabooga/textgen)** — the long-standing general-purpose local LLM web UI; still the backend of choice for several projects above (z-waif included).
- **[vLLM](https://github.com/vllm-project/vllm)** and **[SGLang](https://github.com/sgl-project/sglang)** — high-throughput serving engines, relevant once you're running a companion for more than one user or need low-latency batched inference.
- **[LM Studio](https://lmstudio.ai)** — the most popular local-model GUI/OpenAI-compatible server for non-CLI users.
- **[LiteLLM](https://github.com/BerriAI/litellm)** — a unified API/router across local and hosted LLM providers; the layer that lets a companion swap backends (LM Studio ↔ Ollama ↔ OpenRouter ↔ a hosted API) without touching application code.
- **MLX** (Apple Silicon) and **TensorRT-LLM** (NVIDIA) — hardware-specific inference runtimes worth knowing if you're optimizing for a specific machine.

---

## Open / Roleplay-Tuned Language Models

Base models with strong open weights, plus the community fine-tunes that specifically target character consistency and roleplay over raw benchmark performance.

- **Base model families actively used as companion foundations:** Llama 4 (Meta), Qwen 3 (Alibaba), DeepSeek V3/R1, Mistral Small/Large 3, Gemma 3 (Google) — pick based on your VRAM budget and licensing needs (Qwen and Gemma are generally the most permissively licensed for smaller sizes).
- **[MythoMax-L2-13B](https://huggingface.co/Gryphe/MythoMax-L2-13b)** — long-standing community favorite for roleplay consistency, merges Llama-2 and Huginn lineages; still widely used via [GGUF quantizations](https://huggingface.co/TheBloke/MythoMax-L2-13B-GGUF).
- Other well-regarded roleplay/character fine-tunes worth searching Hugging Face for by name: **Fimbulvetr**, **Psyfighter**, **Chronos-Hermes**, and whatever the current top of [r/LocalLLaMA](https://reddit.com/r/LocalLLaMA)'s roleplay-model megathread is — this list turns over faster than any other category here, so treat named models as a starting search term, not a permanent recommendation.
- **[NousResearch Hermes](https://huggingface.co/NousResearch)** line — strong general instruction-following fine-tunes frequently reused as a roleplay base.

---

## Voice: Text-to-Speech

- **[Coqui TTS / XTTS-v2](https://github.com/coqui-ai/TTS)** ★46k — the most widely adopted open TTS toolkit; XTTS-v2 specifically is the default choice for fast voice cloning from a short sample.
- **[Kokoro-82M](https://huggingface.co/hexgrad/Kokoro-82M)** ★8k (repo) — small (82M param), fast, Apache-2.0 TTS model; a common default for local-first, CPU-friendly companion voices (used by YuriOS, among others).
- **[GPT-SoVITS](https://github.com/RVC-Boss/GPT-SoVITS)** — few-shot voice cloning with strong quality-per-sample-of-reference-audio; a popular choice specifically for cloning an anime/VTuber-style voice.
- **[RVC (Retrieval-based Voice Conversion)](https://github.com/RVC-Project/Retrieval-based-Voice-Conversion-WebUI)** ★37k — real-time-capable voice conversion; "train a good VC model with ≤10 min of data." Frequently paired with a separate TTS engine as a voice-conversion pass.
- **[Bark](https://github.com/suno-ai/bark)** ★39k — text-prompted generative audio model; expressive (laughs, sighs, tone) but heavier and less controllable than the above.
- **[StyleTTS2](https://github.com/yl4579/StyleTTS2)**, **[Orpheus](https://huggingface.co/canopylabs/orpheus-3b-0.1-ft)**, **[MeloTTS](https://github.com/myshell-ai/MeloTTS)**, **[OpenVoice](https://github.com/myshell-ai/OpenVoice)** ★37k, **[Resemble Chatterbox](https://github.com/resemble-ai/chatterbox)** ★26k — other actively-used open TTS/voice-cloning engines, each with different latency/quality/expressiveness trade-offs worth A/B testing for your specific character voice.

---

## Voice: Speech-to-Text & Turn-Taking

- **[Whisper](https://github.com/openai/whisper)** ★106k / **[faster-whisper](https://github.com/SYSTRAN/faster-whisper)** ★25k — the default open STT stack; faster-whisper (CTranslate2-backed) is what most real-time companion projects actually deploy for latency reasons.
- **[Silero VAD](https://github.com/snakers4/silero-vad)** ★9.7k — the standard lightweight voice-activity-detector for deciding when the user has actually stopped talking; load-bearing for any "hands-free" voice loop.
- **[RealtimeTTS](https://github.com/KoljaB/RealtimeTTS)** / **RealtimeSTT** (same author) — streaming wrappers around the above that specifically target low first-byte latency for conversational use.
- Nvidia **Parakeet/Canary** — newer, very fast open STT models worth benchmarking against faster-whisper if latency is your bottleneck.

---

## Embodiment: Avatars, VTubing & Motion

- **[VTube Studio](https://store.steampowered.com/app/1325860/VTube_Studio/)** + its **[public API](https://github.com/DenchiSoft/VTubeStudio)** — the dominant Live2D tracking/animation app; nearly every project above that has a 2D face drives it through this API (see [VTubeStudioJS](https://github.com/Hawkbat/VTubeStudioJS) and the [VTube Studio MCP server](https://github.com/hkopenai/vtube-studio-plugin-mcp-server) for programmatic control).
- **[VMC Protocol](https://protocol.vmc.info/)** ([sh-akira/VirtualMotionCapture](https://github.com/sh-akira/VirtualMotionCapture)) — MIT-licensed OSC-over-UDP protocol for streaming avatar motion between apps; the closest thing this space has to a universal wire format. Senders include VSeeFace/Waidayo/MocapForAll; receivers include Warudo/VNyan/EVMC4U/three-vrm.
- **[three-vrm](https://github.com/pixiv/three-vrm)** ★2k + **[VRM specification](https://github.com/vrm-c/vrm-specification)** — the standard 3D humanoid avatar format for web/three.js-based companions, plus its Unity counterpart **UniVRM**.
- **[VRoid Studio](https://vroid.com/en/studio)** / **[VRoid Hub](https://hub.vroid.com)** — the easiest free tool for making (and sharing) your own VRM avatar without 3D modeling skills.
- **[Live2D Cubism](https://www.live2d.com/en/)** (Editor + SDK) — the standard 2D "paper puppet" animation format for VTuber-style faces; proprietary runtime but an SDK, not a subscription, and the de facto standard here.
- **Warudo**, **VNyan**, **VSeeFace** — VRM/3D avatar rigs and streaming tools, each supporting VMC-protocol input from a companion backend.
- **[vrm-samples](https://github.com/madjin/vrm-samples)** — a curated collection of openly-licensed VRM avatar models to start from instead of commissioning one.
- **[CharacterStudio](https://github.com/M3-org/CharacterStudio)** — open-source VRM avatar creation/customization tool.
- **ARKit blendshapes** (52-shape standard) — the de facto facial-expression interchange format if you're doing camera-based face tracking (iPhone or otherwise) to drive an avatar.

---

## Image & Video Generation

Useful for character art, expression sheets, promotional material, or dynamically generated scenes.

- **[ComfyUI](https://github.com/Comfy-Org/ComfyUI)** — node-based Stable Diffusion workflow tool; the most flexible and now the de facto standard for anyone doing non-trivial image-gen pipelines (LoRA stacking, ControlNet, batch expression generation).
- **[AUTOMATIC1111 / stable-diffusion-webui](https://github.com/AUTOMATIC1111/stable-diffusion-webui)** ★164k — the original and still most-used simple web UI for Stable Diffusion; a gentler on-ramp than ComfyUI.
- **[Fooocus](https://github.com/lllyasviel/Fooocus)** ★51k — "focus on prompting," a much simpler SDXL UI if ComfyUI/A1111's complexity isn't worth it for your use case.
- **Model families:** SDXL, Flux, SD3 (open-weight, ComfyUI/A1111-compatible) and **NovelAI** (proprietary but the historically dominant anime-style checkpoint lineage almost everything else in this niche descends from).
- **[Civitai](https://civitai.com)** — the primary source for downloading the checkpoints/LoRAs above: base models, character/style LoRAs, embeddings, and ControlNet/VAE add-ons for SDXL, Flux, SD3, and NovelAI-descended anime models; see also [Communities & Websites](#communities--websites) below for its community role.

---

## Character Formats & Persona Standards

- **[Character Card Spec V3](https://github.com/kwaroran/character-card-spec-v3)** — the current character-card interchange standard; supersedes V2.
- **[Character Card Spec V2](https://github.com/malfoyslastname/character-card-spec-v2)** — still widely supported for backward compatibility across frontends.
- **[SillyTavern World Info docs](https://docs.sillytavern.app/usage/core-concepts/worldinfo/)** — the reference explanation of lorebook/world-info mechanics (keyword-triggered context injection), which most companion memory systems reinvent in some form.
- **[AICharacterCards.com](https://aicharactercards.com)** — the largest public repository of ready-made character cards in the V2/V3 format.

---

## Character Card Explorers & Repositories

Sites for browsing and downloading ready-made character cards (PNG/JSON, V2/V3 spec) that drop straight into SillyTavern or any compatible frontend.

- **[Chub.ai / CharacterHub](https://chub.ai)** — see [Character Formats](#character-formats--persona-standards) above; the largest and most actively moderated card repository, with V2/V3 filtering.
- **[AICharacterCards.com](https://aicharactercards.com)** — see above; large curated V2/V3 card library.
- **[CharaVault](https://charavault.net)** — a 195k+ card preservation archive with direct PNG/JSON downloads, moderated uploads, and a public API.
- **[RisuRealm](https://realm.risuai.net)** — the card-sharing hub for RisuAI; supports V2, V3, and CHARX card downloads alongside lorebooks and presets.
- **[Pygmalion.chat](https://pygmalion.chat)** — PygmalionAI's own card library; cards are explicitly designed to import/export without lock-in.
- **[Datacat](https://datacat.run/characters/recent)** — a tag-browsable index of public character cards.
- **[JanitorAI](https://janitorai.com)** — a huge closed roleplay platform with an enormous card catalog; it has no native export button, so pulling a SillyTavern-compatible PNG requires a third-party tool like [jai-card-extractor](https://github.com/erpocalypse/jai-card-extractor) or a similar userscript/extension.

---

## Frontends & Chat Clients

- **[SillyTavern](https://github.com/SillyTavern/SillyTavern)** ★31k — see above; the dominant self-hosted roleplay frontend, with a large extension ecosystem (see [SillyTavern-CharacterLibrary](https://github.com/Sillyanonymous/SillyTavern-CharacterLibrary) as one example).
- **[Open WebUI](https://github.com/open-webui/open-webui)** — general-purpose self-hosted LLM chat UI; less roleplay-specialized than SillyTavern but a clean base if you're building your own layer on top.
- **[aituber-kit](https://github.com/tegnike/aituber-kit)** — see Full-Stack Projects above; doubles as a frontend if you just want the web chat layer.

---

## Fine-Tuning, Datasets & Synthetic Data

If prompting and RAG aren't getting your companion's voice consistent enough, this is the next rung up.

- **[Axolotl](https://github.com/axolotl-ai-cloud/axolotl)** and **[LlamaFactory](https://github.com/hiyouga/LlamaFactory)** — the two most popular open fine-tuning frameworks (LoRA/QLoRA/full fine-tune) for adapting a base model to a specific character voice.
- **[distilabel](https://github.com/argilla-io/distilabel)** and **[synthetic-data-generator](https://github.com/argilla-io/synthetic-data-generator)** (Argilla) — pipelines for generating synthetic training/preference data, relevant if you're building an SFT/DPO dataset from your companion's own conversation logs.
- **[Magpie](https://github.com/magpie-align/magpie)** — a method for generating high-quality instruction data directly from an aligned model, no seed prompts needed.
- **Companion-relevant datasets on Hugging Face:** [PygmalionAI/PIPPA](https://huggingface.co/datasets/PygmalionAI/PIPPA) (roleplay conversation corpus), [lemonilia/LimaRP](https://huggingface.co/datasets/lemonilia/LimaRP), `taozi555/rp-opus`.
- **[awesome-instruction-datasets](https://github.com/jianzhnie/awesome-instruction-datasets)** and **[mlabonne/llm-datasets](https://github.com/mlabonne/llm-datasets)** — curated indexes of instruction/fine-tuning datasets more broadly.
- **[Lorebooks as active scenario/character guidance](https://huggingface.co/sphiratrioth666/Lorebooks_as_ACTIVE_scenario_and_character_guidance_tool)** — a widely-referenced practical guide to using SillyTavern-style lorebooks as a cheaper alternative to fine-tuning.

---

## Papers, Guides & Reading

- **[Anthropic — "Building Effective Agents"](https://www.anthropic.com/research/building-effective-agents)** and **["Introducing MCP"](https://www.anthropic.com/news/model-context-protocol)** — the most-cited practical framing for agent architecture generally.
- **MemGPT** — Packer et al., [arXiv:2310.08560](https://arxiv.org/abs/2310.08560) — foundational memory-management paper (became Letta).
- **"Lost in the Middle"** — Liu et al., 2023 — why naively stuffing context windows degrades recall; motivates most memory-retrieval design in this space.
- **ReAct** — Yao et al., 2023 — the reasoning+acting pattern nearly all tool-using agents implement in some form.
- **"Eliza: A Web3-friendly AI Agent Operating System"** — [arXiv:2501.06781](https://arxiv.org/abs/2501.06781) — the ElizaOS paper.
- **Foundational ML papers worth knowing if you're going past prompting into fine-tuning:** "Attention Is All You Need," the Chinchilla scaling paper, LoRA, QLoRA, DPO, KTO, ORPO, InstructGPT/RLHF.
- **[The Agentic Waifu Codex](#yurios--my-project)** — see above; its Appendix C reading list and Appendix B tools/stacks table are the direct source for a large share of this document.

---

## Other Awesome Lists

Already linked above in [Prior Art](#prior-art-the-lists-this-one-stands-on) — repeated here for completeness of the table of contents: [awesome-ai-vtubers](https://github.com/proj-airi/awesome-ai-vtubers), [Awesome-AI-Waifu](https://github.com/parallelarc/Awesome-AI-Waifu), [awesome-oss-monetization](https://github.com/PayDevs/awesome-oss-monetization).

---

## Communities & Websites

- **[r/LocalLLaMA](https://reddit.com/r/LocalLLaMA)** — the center of gravity for local-model discussion generally; essential even though not companion-specific.
- **[SillyTavern Discord](https://sillytavern.app)** and **[r/SillyTavernAI](https://reddit.com/r/SillyTavernAI)** — the largest roleplay-frontend community; most practical "how do I actually get good outputs" knowledge lives here.
- **[Civitai](https://civitai.com)** — the largest hub for Stable Diffusion checkpoints/LoRAs (character likenesses, art styles) and increasingly also for character-adjacent tools; useful for the image-gen half of a companion's identity; see also [Image & Video Generation](#image--video-generation) above for its role as a model source.
- **[Chub.ai / CharacterHub](https://chub.ai)** and **[AICharacterCards.com](https://aicharactercards.com)** — the largest public character-card repositories/communities; see [Character Card Explorers & Repositories](#character-card-explorers--repositories) above for the full list of card sources.
- **r/AICompanions, r/AIRomance, r/MyBoyfriendIsAI** — user-side (not developer-side) communities discussing the companion-relationship experience itself; valuable if you want to understand what people actually want from these products, as distinct from what's technically interesting to build.
- **r/VirtualYoutubers, r/AIVtuber** — VTuber-culture-side communities, useful for the embodiment/streaming half of this space.
- **VRoid Hub / Pixiv VRM communities** and **VRChat community** — avatar-asset and 3D-embodiment communities.
- **Hugging Face forums/Discord** — model- and dataset-specific discussion.
- *(Deliberately not linked as chat platforms: Character.AI, Replika, Kindroid, and similar closed products — mentioned only where relevant above as points of comparison, since this list's focus is open, self-hostable tooling. JanitorAI is the exception, linked above solely as a card source.)*

---

## Notable AI VTubers / Streamers

Not open source, but essential context — this is the "why" behind most of the projects above.

- **[Neuro-sama](https://www.youtube.com/@Neurosama)** (created and operated by **Vedal**, [@vedal987](https://www.youtube.com/user/Vedal987)) — the AI VTuber that essentially created this genre: an LLM-driven virtual streamer that plays games (osu!, Minecraft, Pokémon), sings, and banters live with chat, live since December 2022. Fully closed/proprietary, but the reference point nearly every project above (AIRI, kimjammer/Neuro, my-neuro, AIwaifu) explicitly cites as what they're trying to recreate in the open.

---

## YouTube Channels

- **[SugarcaneDefender](https://www.youtube.com/@SugarcaneDefender)** — creator of [z-waif](https://github.com/SugarcaneDefender/z-waif); build/install/tutorial videos for assembling a fully local AI waifu (Oobabooga + RVC + Whisper + VTube Studio). One of the few channels documenting the DIY local-companion build process end to end rather than reviewing closed apps.
- **[vedal987 / Neuro-sama](https://www.youtube.com/user/Vedal987)** — see above; not a tutorial channel, but essential viewing for what the finished product looks like at the top of the field.
- **AIRI project DevLogs** ([airi.moeru.ai/docs/en/blog](https://airi.moeru.ai/docs/en/blog/)) — not YouTube, but the closest thing to a running build-log for the most important open project in this space; check here before searching YouTube for AIRI content.
- Search **"AI VTuber tutorial," "Open-LLM-VTuber setup," or "local AI waifu Live2D"** on YouTube for current build-along content — this corner of YouTube turns over quickly (small creators, project-specific setup guides tied to whatever release is current), so a live search will usually beat a static link list here.

---

## Adjacent Reading (not strictly open source)

Proprietary products/platforms mentioned only because they've published something genuinely educational or field-defining:

- **Character.AI** — closed product, but its scale is why "character cards" became a standard interchange format at all; no dev resources worth linking.
- **Replika** — closed, but the most frequently studied case study for long-term AI-relationship dynamics — worth reading about, not building on.
- **NovelAI** — proprietary, but its anime-style Stable Diffusion checkpoints are the historical ancestor of most open anime-art models still in use.

---

## AI-Waifu-Adjacent Media: Anime, TV, Film & Books

The cultural DNA this whole field is downstream of, for when you want to think about the *idea* of an AI companion rather than the implementation.

**Anime & Manga**
- *Chobits* (CLAMP) — the foundational "persocom" text for this entire genre; still the most direct fictional analogue to a physically-embodied personal AI companion.
- *Time of Eve* (Yasuhiro Yoshiura) — android companions and the ethics of treating them as people; probably the single best short work to watch before designing a companion's personality.
- *Ghost in the Shell* (Masamune Shirow / Mamoru Oshii) — foundational for thinking about mind/memory/identity as software, directly upstream of how this list's "memory" section frames things.
- *Plastic Memories* — mortality and memory in android companions; emotionally brutal, relevant to anyone building "the companion remembers you" features.
- *Hyperdimension* / *Sword Art Online: Alicization* arc — AI/digital-consciousness companion tropes, more pulp than the above but influential on the community's imagination.
- *Zenshu*, *Vivy: Fluorite Eye's Song* — more recent entries specifically about AI agency and autonomy, close in theme to the "agentic" framing of this list.

**Film & TV**
- *Her* (2013) — the reference point everyone in this space eventually gets compared to; a genuinely good design document disguised as a movie.
- *Ex Machina* (2014) — the counterpoint to *Her*; agency, deception, and what it means for a companion to have its own goals.
- *Klara and the Sun* (2026 film, based on the Kazuo Ishiguro novel below) — an android companion story about devotion and the limits of care.
- *Westworld* (HBO) — long-run exploration of embodied AI, memory-editing, and autonomy at a much larger scale.
- *Black Mirror* — several standalone episodes ("Be Right Back," "San Junipero," "Joan Is Awful") are directly about AI/digital companionship and consequence.
- *I Have No Mouth, and I Must Scream* (older, but the essential "what if the mind you built resents you" text) — worth knowing even if not literally about companions.

**Books**
- *Klara and the Sun* — Kazuo Ishiguro. A solar-powered android companion narrates her own purchase and purpose; the best-written recent treatment of devotion-as-design in an artificial mind.
- *Do Androids Dream of Electric Sheep?* — Philip K. Dick. The foundational text for "how do you tell a person from a companion," underlying nearly everything downstream including *Blade Runner*.
- *Machines Like Me* — Ian McEwan. A domestic android-companion story explicitly about the ethics of building something that can suffer.
- *Klara and the Sun*'s nonfiction counterpart, for the technical/ethical side rather than fiction: **The Agentic Waifu Codex** (see [YuriOS section](#yurios--my-project) above) — included here too since it directly addresses the same questions ("what are you actually building, and what do you owe it") from a practitioner's rather than novelist's angle.

---

*Corrections, additions, and disagreements welcome. If you maintain a project listed here and think its placement or description is wrong, open an issue.*
