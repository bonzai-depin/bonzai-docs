# BonzAI Desktop

BonzAI Desktop is the full local AI production studio. It is an Electron application with a Vue renderer, local model backends, wallet integration, P2P inference, companion management, dataset/training flows, and minting/publishing tools.

## Core Capabilities

- Local text generation through OpenClaw's OpenAI-compatible API.
- Image, audio, video, and vision pipelines through the local Flask backend.
- 3D asset generation through AI-generated Three.js code and preview.
- Dataset import and training workflows.
- Content NFT minting.
- Autonomous companion creation, roleplay, minting, wallets, tokens, and social presence.
- P2P consumer/provider modes.
- BONZAI token level detection, unlocks, MintPool participation, and reward claiming.

## Local Backends

| Backend | Default port | Purpose |
| --- | --- | --- |
| OpenClaw | `3002` | OpenAI-compatible LLM chat completions |
| Flask server | `65000` | Image, audio, video, music, and vision endpoints |
| OpenClaw Gateway | `18789` | Multi-channel chat and webhook orchestration |

## Generation Surfaces

| Surface | Examples |
| --- | --- |
| Text | LLM chat, companion replies, prompt rewriting, skill execution |
| Image | FLUX/SDXL/Z-Image style pipelines depending on mode |
| Audio | Kokoro fast TTS, Qwen persona TTS, ACE-Step music |
| Video | LTX-2 text-to-video and image-to-video |
| Vision | Qwen-style visual analysis endpoint |
| 3D | Generated Three.js scene/code rather than TRELLIS-style mesh generation |

## Onchain Actions

Desktop is where most economic actions happen:

- Connect wallet.
- Check BONZAI balance and level.
- Mint content NFTs.
- Mint companions.
- Launch companion tokens.
- Launch fine-tune/model tokens.
- Register as a provider.
- Record/claim provider rewards.
- Register/claim MintPool holder rewards.
- Publish contribution, dataset, model, or evaluation records when registry addresses are configured.

## Contribution Studio

Desktop imports BonzAI+ contribution packs and turns them into a local ledger. It can validate records, preview samples, score quality, split train/eval material, attach contributor metadata, and prepare publishable assets.

The publish path depends on registry addresses and IPFS metadata upload configuration. BonzAI does not use Irys.
