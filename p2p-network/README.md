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

## Inference Modes

### Standard (v1) — Fast, Trust-Based

Single provider processes the full request. Fast but provider sees everything.

### Private Pipeline (v2) — Structurally Private

Splits inference across multiple peers via pipeline parallelism. No single peer sees the prompt or output. Uses llama.cpp's RPC backend tunneled through libp2p. See [Private Inference](private-inference.md) for details.

## Contracts

| Contract | Address | Purpose |
|----------|---------|---------|
| BonzaiProviderRegistry | [`0x683d0B11...`](https://basescan.org/address/0x683d0B11a2553E9D4B338935e2D935873439e8bB) | Registration, staking, shard capabilities |
| BonzaiPayment | [`0x438A73FC...`](https://basescan.org/address/0x438A73FC0e0DA882BFdD007aF41415769Af33F1d) | Single-provider ETH/USDC payments (x402) |
| BonzaiPipelinePayment | [`0xB45D1D63...`](https://basescan.org/address/0xB45D1D635192Aa223Ce28d9F3cC047A13D8850Bd) | Multi-payee atomic pipeline payments |

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
| 11 | PIPELINE_SHARD | Pipeline shard provider (private inference) |

## Platform Fee

A **2.5% platform fee** is deducted from all paid inference and sent to the treasury.
