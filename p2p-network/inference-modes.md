# Network Inference Modes

BonzAI supports three network modes that determine how inference requests are routed. All generation types (image, speech, music, video, LLM) follow the same routing logic. The only exception is pipeline parallelism, which currently applies to LLM only.

---

## Modes Overview

| Mode | Role | Inference Routing |
|---|---|---|
| **Local** | Solo user | All inference runs on your machine |
| **Consumer** | Client | Routed to selected providers (LAN or remote) |
| **Provider** | Server | Runs locally + serves remote peers |

Configure in **P2P Network** settings (bottom bar > P2P button).

---

## Local Mode

Default mode. All inference hits your local servers:

- **LLM**: OpenClaw on port 3002 (node-llama-cpp)
- **Image/Audio/Video/Music/Vision**: Flask on port 65000

No P2P node is started. No network traffic.

---

## Consumer Mode

You consume inference from other BonzAI nodes on the network.

### Step 1: Start P2P

1. Select **Consumer** in the network mode selector
2. Click **Start Node**
3. Wait for P2P to connect (peer ID appears)

### Step 2: Select Providers

LAN providers appear automatically under **Local Network Providers** (discovered via mDNS). Remote providers appear under **Remote Providers** (discovered via on-chain registry).

- **Click a provider card** to add it to your selection
- **Click again** to deselect
- **Select multiple** providers for redundancy — requests are randomized across them

Each provider card shows:
- IP address (LAN) or peer ID (remote)
- Latency (ms)
- Version
- Supported pipelines
- LAN/FREE tags for local network providers

### Step 3: Enable Pipeline Parallelism (Optional, LLM Only)

For private distributed LLM inference:

1. In the **Private Mode** section (consumer mode), click **Enable**
2. Configure **Privacy Level** (local proportion, 25% default)
3. Optionally enable **Extra Privacy** (differential privacy noise)

When enabled:
- LLM requests split across your GPU + provider RPC shards
- Your llama-server runs locally with `--rpc` pointing at remote shards
- Providers process partial tensor operations without seeing your prompt
- Non-LLM requests (image, audio, etc.) still route normally to a random provider

### How Routing Works

```
inference-request (main.js)
  |
  |- mode = local/provider -> local Flask/OpenClaw
  |
  '- mode = consumer
       |
       |- pipeline + LLM -> orchestrator (all providers as RPC shards)
       |
       '- no pipeline OR non-LLM
            -> random provider from selection
            -> if all fail -> fallback to local
```

---

## Provider Mode

You share your GPU with the network and earn from inference.

### Step 1: Configure Pricing

1. Select **Provider** in the network mode selector
2. Choose payment currency: **Free**, **ETH**, or **USDC**
3. If not Free, set per-pipeline prices (Chat per 1K tokens, Image per image, etc.)

When **Free** is selected, the pricing grid is hidden — all inference is free for consumers.

### Step 2: Start Node

Click **Start Node**. This starts:

- **P2P node** (libp2p with mDNS for LAN discovery)
- **rpc-server** on port 50052 (for pipeline parallelism shards)

Both start automatically — no separate toggle needed.

### What Happens on Your Machine

Your node handles two types of incoming requests:

1. **Standard inference**: Consumer sends a full request → your Flask/OpenClaw processes it → result returned via P2P
2. **Pipeline shard**: Consumer's llama-server connects to your rpc-server → you process partial tensor operations → consumer assembles the full response

You never choose which mode — the consumer's request determines it. If they're running pipeline parallelism, your rpc-server handles it. If not, your standard inference handler responds.

### LAN Providers

When your P2P node starts, mDNS broadcasts your presence on the local network. Any BonzAI consumer on the same LAN discovers you automatically within 10 seconds. LAN inference is always free — no payment, no on-chain registration needed.

A desktop notification appears on consumer machines when they discover you.

---

## Network Mode Tags

Every generation is tagged with how it was processed:

| Tag | Meaning | Display |
|---|---|---|
| `local` | Processed on your machine | No tag shown |
| `remote` | Processed by a selected provider | Blue "Remote" pill |
| `private` | Processed via pipeline parallelism | Green "Private" pill |

Tags are stored with each inference record and displayed in generation history.

---

## OpenClaw & Hermes Integration

Network mode applies to all inference entry points — including OpenClaw webhooks and Hermes messaging platforms. If you're in consumer mode with providers selected, a WhatsApp message that triggers image generation will route to your selected provider, same as if you generated from the desktop UI.

Check your current network status from any connected platform:

```
!bonzai network
```

This shows: mode, P2P status, selected providers, and available pipelines. Network configuration is read-only from chat — all settings are managed in the BonzAI desktop application.
