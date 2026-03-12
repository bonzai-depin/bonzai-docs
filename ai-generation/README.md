# AI Generation

BonzAI provides **free, unlimited, local** AI generation across six modalities. All inference runs on your machine — nothing is sent to external servers.

## Pipelines

| Modality | Models | Local Port |
|----------|--------|------------|
| [Text (LLM)](text.md) | 21 models via OpenClaw | 3002 |
| [Image](image.md) | 4 pipelines (FLUX, SDXL, Z-Image) | 65000 |
| [Audio & Music](audio.md) | Kokoro TTS, Qwen3-TTS, ACE-Step | 65000 |
| [Video](video.md) | LTX-2 (text-to-video, image-to-video) | 65000 |
| [3D](3d.md) | AI-generated Three.js code | — |

## How It Works

BonzAI runs two local inference backends:

1. **OpenClaw** (port 3002) — Handles all LLM text generation via an OpenAI-compatible API (`/v1/chat/completions`)
2. **Flask Server** (port 65000) — Handles image, audio, music, video, and vision pipelines

Models are downloaded on first use to `~/bonzai-models/` and cached for future sessions.

## Generation vs. Minting

**All generation is free** — you don't need tokens or a wallet to use any AI pipeline.

Levels (requiring BONZAI token holdings) only gate **minting** your generated content as NFTs. See [Token & Levels](../web3/token-levels.md) for details.
