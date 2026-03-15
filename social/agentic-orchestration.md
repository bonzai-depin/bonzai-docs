# Agentic Orchestration

BonzAI integrates with two orchestration backends that extend companion capabilities beyond the desktop app: **OpenClaw** and **Hermes Agent**. These let your companions respond to messages on WhatsApp, Telegram, Discord, and Mattermost — using the same AI pipelines as the desktop UI.

## How It Works

```
External message (WhatsApp/Telegram/Discord/Mattermost)
  → OpenClaw Gateway (port 18789)
    → BonzAI webhook handler
      → Companion response (text + image + audio + video)
        → Reply sent back to channel
```

Messages from external platforms are forwarded to the BonzAI renderer via IPC, processed through the same companion response pipeline as the desktop app, and sent back. Your companion's personality, voice, and visual style are consistent across all channels.

## OpenClaw

OpenClaw runs on port 3002 and provides:

- **OpenAI-compatible LLM API** at `/v1/chat/completions`
- **Multi-channel webhook gateway** on port 18789
- **SKILL.md-based skill system** for registering BonzAI capabilities

### How BonzAI Integrates with OpenClaw

When you enable OpenClaw in BonzAI, the app:

1. Updates `~/.openclaw/agents/main/agent/models.json` with a BonzAI provider:
   - Base URL: `http://127.0.0.1:3002/v1`
   - API format: `openai-completions`
   - Model ID: `bonzai/bonzai-sovereign`
2. Sets BonzAI as the default model in `~/.openclaw/openclaw.json`
3. Configures Claude Sonnet as a fallback model

This means any LLM request through OpenClaw (from any channel) routes to your local BonzAI inference engine.

### Supported Channels

| Channel | Setup |
|---------|-------|
| **WhatsApp** | QR code pairing via OpenClaw |
| **Telegram** | Bot token configuration |
| **Discord** | Bot token + server invite |
| **Mattermost** | Plugin installation |

Each channel connects through the gateway at `localhost:18789`. Messages are routed to BonzAI's webhook handler for processing.

## Hermes Agent

[Hermes Agent](https://hermes-agent.nousresearch.com/docs/) by Nous Research is an alternative orchestrator with the same capabilities.

### How BonzAI Integrates with Hermes

When you enable Hermes in BonzAI, the app:

1. Creates the directory `~/.hermes/skills/ai/bonzai/`
2. Installs a **SKILL.md** file that registers all BonzAI capabilities:
   - All LLM model endpoints
   - Image, audio, video, and vision pipeline access
   - Companion management commands
   - Webhook command routing
3. Adds environment variables to `~/.hermes/.env`:
   - `BONZAI_BASE_URL` — Flask server endpoint
   - `BONZAI_API_KEY` — Local API key

## Enabling Orchestration

### Step 1: Install OpenClaw or Hermes

Install either orchestrator on your system:
- **OpenClaw**: Follow the [OpenClaw installation guide](https://openclaw.dev)
- **Hermes**: Follow the [Hermes Agent docs](https://hermes-agent.nousresearch.com/docs/)

### Step 2: Enable in BonzAI

1. Open **Network Settings** (gear icon in the bottom bar)
2. Scroll to **Agentic Orchestration**
3. You'll see status indicators for each orchestrator:
   - "Not installed" — The orchestrator isn't detected on your system
   - **Enable** / **Disable** toggle — Click to activate or deactivate
4. Click **Enable** on your preferred orchestrator

Both orchestrators can run side by side without conflict.

### Step 3: Connect a Channel

Follow your orchestrator's docs to connect a messaging platform (WhatsApp, Telegram, etc.). Once connected, messages from that platform flow through BonzAI automatically.

## Webhook Commands

When messaging a BonzAI-connected channel, these commands are available:

### Companion Chat

```
!companion list              — List all 13 default companions
!companion select <name>     — Select a companion for this channel
```

Once a companion is selected, any unprefixed message triggers a companion response with text, optional voice audio, and optional generated images.

### Generation Commands

```
!generate image <prompt>           — Generate an image (FLUX Klein turbo)
!generate image_quality <prompt>   — Generate a quality image (Z-Image Turbo)
!generate image_standard <prompt>  — Generate an SDXL image (uncensored)
!generate audio <text>             — Text-to-speech (Kokoro turbo)
!generate video <prompt>           — Generate a video (LTX-2)
!generate music <prompt>           — Generate music (ACE-Step)
!generate vision                   — Analyze an attached image (Qwen3-VL)
```

### Companion Minting

```
!mint bare                   — Mint a bare companion NFT instantly (0.25 ETH)
!mint bare female            — Mint bare with specified gender
!mint companion <name>       — Mint with full AI-generated personality + portrait
!mint status                 — Show your owned companions and token IDs
!mint finalize <tokenId>     — Complete a bare companion's setup
```

`!mint bare` is instant — no AI generation needed. `!mint companion` requires BonzAI Desktop to be running for portrait and personality generation.

### Skills

```
!skill list                  — List available skills
!skill list <category>       — Filter skills by category
!skill run <id> [key=value]  — Execute a skill
```

### Model Management

```
!model <name>                — Load a specific LLM model
!model restore               — Restore the previous model
```

### Provider Discovery

```
!providers                   — List P2P inference providers on the network
!marketplace                 — Browse available skills for purchase
```

## Message Formatting

Companion responses are formatted per-platform:

| Platform | Max Length | Image Support | Audio Support |
|----------|-----------|---------------|---------------|
| WhatsApp | 4,096 chars | Yes (file path) | Yes (file path) |
| Discord | 2,000 chars | Yes (embed) | Yes (attachment) |
| Telegram | 4,096 chars | Yes (file) | Yes (voice) |
| Mattermost | 4,000 chars | Yes (file) | Yes (file) |

Emotion tags in companion responses are mapped to emoji/color indicators automatically.

## Architecture

```
┌──────────────────────────────────────────────────────────────┐
│ External Platforms (WhatsApp / Telegram / Discord)           │
└──────────────────────┬───────────────────────────────────────┘
                       │ Webhook
┌──────────────────────▼───────────────────────────────────────┐
│ OpenClaw Gateway (:18789) or Hermes Agent                    │
└──────────────────────┬───────────────────────────────────────┘
                       │ IPC (onOpenClawWebhook)
┌──────────────────────▼───────────────────────────────────────┐
│ BonzAI Main Process (Electron)                               │
│  → openclaw.handler.js                                       │
│    → Command parsing (!generate, !mint, !companion, etc.)    │
│    → Companion personality + LLM response                    │
│    → Flask pipeline calls (image, audio, video, vision)      │
└──────────────────────┬───────────────────────────────────────┘
                       │ HTTP
┌──────────────────────▼───────────────────────────────────────┐
│ Inference Backends                                           │
│  ├─ OpenClaw LLM (:3002) — 21 models, OpenAI-compatible     │
│  └─ Flask (:65000) — Image / Audio / Video / Vision          │
└──────────────────────────────────────────────────────────────┘
```
