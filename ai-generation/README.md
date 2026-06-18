# AI Generation

BonzAI generation is local-first. Normal generation is free and does not require a wallet. Wallets and BONZAI levels matter when the user mints, publishes, participates in pools, launches tokens, or claims rewards.

## Product Surfaces

| Product | Generation role |
| --- | --- |
| BonzAI Web | Browser local chat where supported |
| BonzAI+ | Side-panel chat, live video/screen understanding, in-browser image generation, dataset smart analysis |
| BonzAI Desktop | Full local generation studio for text, image, audio, music, video, vision, and 3D scene generation |

## Desktop Pipelines

| Type | Backend | Notes |
| --- | --- | --- |
| Text | OpenClaw | OpenAI-compatible chat completions through the local OpenClaw server |
| Image | Flask | Turbo, quality, standard, and advanced image endpoints |
| Audio | Flask | Kokoro fast TTS, Qwen-style persona TTS |
| Music | Flask | ACE-Step music generation |
| Video | Flask | LTX-2 text-to-video and image-to-video |
| Vision | Flask | Visual analysis endpoint |
| 3D | Renderer + LLM | AI-generated Three.js code and WebGL preview, not TRELLIS mesh generation |

## Minting Generated Outputs

Generated outputs can remain private. If the user chooses to mint:

1. Desktop checks wallet and BONZAI level/unlock status.
2. Metadata/media is uploaded to IPFS/Pinata or configured IPFS-compatible storage.
3. The user confirms the mint transaction.
4. Fees route according to the content type and reward structure.

BonzAI does not use Irys.
