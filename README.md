# Welcome to BonzAI

**BonzAI** is a decentralized, privacy-preserving desktop application that combines AI inference, blockchain integration, and a peer-to-peer network into a single platform.

All AI generation runs **locally on your machine** — your data never leaves your device.

## What You Can Do

- **Generate** text, images, audio, music, video, and 3D assets using state-of-the-art open-source models
- **Mint** your AI-generated content as NFTs on Base and LUKSO
- **Create** AI companions with on-chain identity (ERC-8004), autonomous wallets, and personality
- **Earn** by sharing your GPU with the P2P inference network
- **Trade** companion and model tokens on Uniswap V4 with custom hook fee distribution

## Key Principles

| Principle | What It Means |
|-----------|---------------|
| **Local-First** | All inference runs on your hardware. No cloud dependency. |
| **Free Generation** | Every AI pipeline is free to use. Levels only gate NFT minting. |
| **Multi-Chain** | Ethereum, Arbitrum, Base, and LUKSO supported. |
| **Open Models** | 21 LLMs, 4 image pipelines, TTS, music, video, and vision — all open-source. |
| **Self-Custody** | Your wallet, your keys. Companions get their own deterministic wallets. |

## Architecture at a Glance

```
Vue 3 Renderer  ←→  Electron Main Process  ←→  Inference Backends
  (UI + Pinia)        (IPC, P2P, Store)         (OpenClaw :3002, Flask :65000)
       ↕                    ↕
   Web3 Services        Python ML Server
  (Base, LUKSO)       (Image, Audio, Video)
```

## Links

- **Website**: [bonzai.sh](https://bonzai.sh)
- **Token**: BONZAI on [Ethereum](https://etherscan.io/token/0xDdA9Ff241C7160be8295EF9Eca2e782361467666) · [Base](https://basescan.org/token/0xc4d137def384ee0f8857887f5950669ba04984ec) · [Arbitrum](https://arbiscan.io/token/0x0a84edf70f30325151631ce7a61307d1f4d619a3)
- **Companion NFT**: [BaseScan](https://basescan.org/address/0xb3ea09922E8227cCa6331346ed31D0f5F173BDe3)
