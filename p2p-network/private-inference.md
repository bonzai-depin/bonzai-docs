# Private Inference (Pipeline Parallelism)

BonzAI's pipeline parallelism protocol (`/bonzai/v2/pipeline`) splits LLM inference across multiple peers so **no single peer sees your prompt or output**. Privacy is structural — achieved through architecture, not cryptography or trusted hardware.

## The Inference Trilemma

Every decentralized AI inference system faces a three-way tradeoff:

| Property | Description |
|----------|-------------|
| **Speed** | Low-latency inference comparable to centralized providers |
| **Privacy** | No entity in the pipeline can see the prompt or output |
| **Decentralization** | Anyone with consumer hardware can participate |

Existing approaches sacrifice one vertex:

| Approach | Speed | Privacy | Decentralized | Sacrifices |
|----------|-------|---------|---------------|------------|
| TEE (Chutes, Nillion, Phala) | Fast | Private | Datacenter only | Decentralization |
| FHE / MPC | 1000x slower | Private | Any hardware | Speed |
| Single-provider P2P (v1) | Fast | Provider sees all | Any hardware | Privacy |
| Venice.ai | Fast | Trust/TEE tiers | Centralized | Decentralization |
| **BonzAI Pipeline (v2)** | **Moderate** | **Structural** | **Any GPU** | **None (bends the triangle)** |

## How It Works

BonzAI uses llama.cpp's native RPC backend to distribute model layers across peers, tunneled through the libp2p P2P network.

```
┌──────────────────────────────────────────────────────────────┐
│ Your Device (BonzAI Electron)                                │
│                                                              │
│  llama-server --rpc peer1:port,peer2:port                   │
│  --tensor-split 25,37,38 --split-mode layer                 │
│                                                              │
│  First k layers (local) + Last r layers (local)             │
│  = Tokenizer, embedding, unembedding, sampling              │
│    NEVER leave your device                                   │
└────────────────────────┬─────────────────────────────────────┘
                         │ TCP tunneled through libp2p
           ┌─────────────┼─────────────┐
      ┌────▼────┐   ┌────▼────┐   ┌────▼────┐
      │ Peer A   │   │ Peer B   │   │ Peer C   │
      │rpc-server│   │rpc-server│   │rpc-server│
      │(GPU/CPU) │   │(GPU/CPU) │   │(GPU/CPU) │
      └─────────┘   └─────────┘   └─────────┘
      Only sees        Only sees      Only sees
      opaque tensor    opaque tensor  opaque tensor
      operations       operations     operations
```

### What stays on your device

- Tokenizer (text to token IDs)
- Embedding layer (token IDs to vectors)
- First k transformer layers (privacy boundary)
- Last r transformer layers (privacy boundary)
- Unembedding (vectors to token IDs)
- Sampling (token selection)
- Detokenization (token IDs to text)

### What remote peers see

- Opaque float16 tensor multiply/add operations
- Tensor dimensions (public model architecture info)
- Timing of operations

### What remote peers NEVER see

- Your prompt text or token IDs
- The generated output text
- The vocabulary or tokenizer
- Your identity (in P2P mode)

## Privacy Hardening

### Differential Privacy Noise (opt-in)

Calibrated Gaussian noise (epsilon-DP) is added to activation tensors before they leave your device. Configurable epsilon:

- **epsilon = 2**: Strong privacy, may reduce output quality
- **epsilon = 8**: Balanced (default)
- **epsilon = 16**: Minimal noise, preserves quality

### Dimension Shuffling (always-on)

Random permutation applied to the hidden dimension of activation tensors before each hop. An attacker must brute-force d! possibilities (d = 4096+) before attempting model inversion.

## Pipeline Payment

Pipeline inference uses the `BonzaiPipelinePayment` contract for atomic multi-payee settlement. The consumer signs ONE EIP-712 message covering all pipeline peers:

- **Contract**: [`0xB45D1D635192Aa223Ce28d9F3cC047A13D8850Bd`](https://basescan.org/address/0xB45D1D635192Aa223Ce28d9F3cC047A13D8850Bd)
- **Domain**: `BonzAI x402` version `2` on Base (8453)
- **Platform fee**: 2.5% deducted from total, remainder distributed proportionally
- **Max providers**: 16 per pipeline session
- **Supports**: ETH (native) and USDC

## How to Use

### As a Consumer (Private Inference)

1. Go to **Agents > Network Settings** (Consumer mode)
2. Enable **Pipeline Inference**
3. Enable **Local Test Mode** to test on a single machine
4. Adjust **Local Layer Proportion** (25%-75%)
5. Optionally enable **Differential Privacy Noise**
6. Chat normally — inference routes through the pipeline transparently

### As a Shard Provider

1. Go to **Agents > Network Settings** (Provider mode)
2. Enable **Pipeline Shard Provider**
3. The `rpc-server` binary starts automatically on port 50052
4. Your GPU processes tensor operations for consumers
5. You earn ETH/USDC per inference session

### OpenClaw / Hermes Integration

When pipeline mode is active, all LLM requests through OpenClaw webhooks (WhatsApp, Telegram, Discord) are automatically routed through the privacy pipeline. Commands use the `!bonzai` prefix:

```
!bonzai help              — Show all commands
!bonzai generate image    — Generate an image
!bonzai companion select  — Select a companion
!bonzai status            — Show session status
```

## Technical Details

### Built on llama.cpp

The `rpc-server` and `llama-server` binaries are compiled from the llama.cpp source bundled with node-llama-cpp, with `GGML_RPC=ON` for distributed tensor computation:

- **macOS**: Metal GPU acceleration
- **Windows/Linux**: CUDA GPU acceleration
- **Static linking**: Self-contained binaries, no external dependencies

### TCP-over-libp2p Tunnel

llama.cpp's RPC protocol uses TCP. BonzAI tunnels this through libp2p streams for:

- NAT traversal (Circuit Relay, WebRTC)
- End-to-end encryption (Noise protocol)
- Peer discovery (custom DHT `/bonzai/kad/1.0.0`)

### Session Persistence

The pipeline session (llama-server + tunnels) persists across messages. First message incurs startup cost (~5-10s for Metal shader compilation). Subsequent messages are fast — just the inference time.

## Roadmap

### Phase 2 (Q4 2026 - Q1 2027)

- **Speculative decoding**: 8-19 tok/s (up from 3-5 tok/s)
- **Image pipeline split**: DiT models (FLUX, Z-Image) via PyTorch distributed pipelining
- **Audio/video pipeline split**: Qwen3-TTS, ACE-Step, LTX-2
- **ASN diversity**: Sybil resistance — pipeline peers must be on different autonomous systems
- **MoE routing privacy**: Expert router layers kept within client's local shard
