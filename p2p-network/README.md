# P2P Network

BonzAI supports peer-to-peer distributed inference, allowing users to share GPU resources and earn ETH or USDC for processing AI requests.

## Overview

The P2P network connects consumers (users requesting inference) with providers (users sharing their GPU). Payments are processed on **Base** (chain ID 8453) for cheap gas (~$0.001 per transaction).

## Architecture

```
Consumer                        Provider                       Base Chain
  │                               │                               │
  │── libp2p request ────────────►│                               │
  │◄── 402 Payment Required ──────│                               │
  │── ETH payment ────────────────────────────────────────────►   │
  │── retry with proof ──────────►│                               │
  │                               │── verify payment ────────►    │
  │◄── inference result ──────────│                               │
  │                               │── withdraw earnings ─────►   │
```

## Network Modes

- **Local** (default) — All inference runs on your machine. Free, no payments.
- **Remote (Consumer)** — Send requests to providers on the network. Costs ETH/USDC.
- **Provider** — Share your GPU and earn ETH/USDC for processing requests.

## Contracts

| Contract | Purpose |
|----------|---------|
| BonzaiProviderRegistry | Registration, staking, capability listing |
| BonzaiPayment | ETH/USDC payment processing with EIP-712 signatures |

## Supported Pipelines

Providers can offer any combination of these pipelines:

| ID | Pipeline | Description |
|----|----------|-------------|
| 0 | LLM | Text generation (21 models) |
| 1 | IMAGE_TURBO | Fast image generation |
| 2 | IMAGE_QUALITY | High quality images |
| 3 | IMAGE_STANDARD | Standard diffusion |
| 4 | IMAGE_ADVANCED | Advanced generation |
| 6 | AUDIO_TURBO | Fast TTS |
| 7 | AUDIO_QUALITY | Quality TTS |
| 8 | MUSIC | Music generation |
| 9 | VIDEO_FAST | Video generation |
| 10 | VISION | Vision analysis |

## Platform Fee

A **2.5% platform fee** is deducted from all paid inference and sent to the treasury.
