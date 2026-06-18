# Harness: OpenClaw & Hermes

BonzAI connects to external messaging platforms through two orchestrators: **OpenClaw** for multi-channel chat and **Hermes** for direct messaging integrations. Both route inference through the same unified handler as the desktop UI — your network mode, selected providers, and pipeline settings apply to all platforms.

---

## Architecture

```
WhatsApp / Telegram / Discord / Mattermost
                |
                v
     OpenClaw Gateway (:18789)
     or Hermes Webhook
                |
                v
     IPC -> openclaw.handler.js
                |
                v
     inference-request (unified router)
                |
     +----------+----------+
     |          |          |
   Local    Consumer   Provider
  (Flask)   (P2P)     (Flask)
```

All channels share the same inference routing. The handler reads `p2p.networkMode` from the application store. No network configuration is set from chat — it's always read-only.

---

## OpenClaw

OpenClaw is a multi-channel chat gateway running on port **18789**. It receives webhooks from messaging platforms and forwards them to BonzAI via IPC.

### Supported Channels

| Platform | Protocol | Auth | Notes |
|---|---|---|---|
| WhatsApp | QR code pairing | Phone number | Via WhatsApp Web bridge |
| Telegram | Bot API | Bot token | Slash commands + inline |
| Discord | Bot webhook | Bot token | Embeds, thread history |
| Mattermost | Plugin | Webhook URL | Self-hosted teams |

### Configuration

OpenClaw settings are in `src/config/social.config.js` under `OPENCLAW_CONFIG`:

```js
{
  gateway: { host: '127.0.0.1', port: 18789 },
  sandbox: true,  // Local-only mode
}
```

Webhooks arrive at `http://127.0.0.1:18789/webhook` and are forwarded to the renderer via the `openclaw-webhook` IPC event.

---

## Hermes

Hermes is BonzAI's direct messaging integration. It uses the same command handler as OpenClaw but with the `/bonzai` prefix instead of `!bonzai`.

Both prefixes are interchangeable — the parser accepts either:
```
!bonzai draw a sunset       (OpenClaw convention)
/bonzai draw a sunset       (Hermes convention)
```

---

## Command Reference

### Network Status (Read-Only)

```
!bonzai network
```

Shows full network status: mode, P2P state, selected providers, and available pipelines. All network configuration is managed in the BonzAI desktop application.

### Model Management

| Command | Description |
|---|---|
| `!bonzai model <name>` | Load a specific LLM model |
| `!bonzai model restore` | Restore the model used before companion chat |
| `!bonzai models` | List all available LLM models |

### Companion & Roleplay

| Command | Description |
|---|---|
| `!bonzai companion list` | List available companions |
| `!bonzai companion select <name>` | Select a companion for roleplay |
| `!bonzai scenario list` | List available scenarios |
| `!bonzai scenario select <name>` | Select a scenario |
| `!bonzai settings <option> <value>` | Configure generation settings |
| `!bonzai status` | Show current session (companion, scenario, history) |
| `!bonzai reset` | Clear conversation history |

### AI Generation

| Command | Description |
|---|---|
| `!bonzai generate image <prompt>` | Fast image (FLUX Klein) |
| `!bonzai generate image_quality <prompt>` | Quality image |
| `!bonzai generate image_standard <prompt>` | Standard image (SDXL) |
| `!bonzai generate video <prompt>` | Video (LTX-2) |
| `!bonzai generate audio <text>` | Fast TTS (Kokoro) |
| `!bonzai generate audio_quality <text>` | Quality TTS (Qwen3-TTS) |
| `!bonzai generate music <prompt>` | Music (ACE-Step) |
| `!bonzai generate vision` | Image analysis (Qwen3-VL, attach image) |

### NFT Minting

| Command | Description |
|---|---|
| `!bonzai mint bare [gender]` | Mint a bare companion NFT on the configured app chain |
| `!bonzai mint companion <name>` | Mint a complete companion with metadata |
| `!bonzai mint status` | Check mint status and owned companions |
| `!bonzai mint finalize <tokenId>` | Finalize a bare companion setup |

### Autonomous Mode

| Command | Description |
|---|---|
| `!bonzai autonomous on` | Enable autonomous companion actions |
| `!bonzai autonomous off` | Disable autonomous mode |
| `!bonzai autonomous status` | Show config and current state |
| `!bonzai autonomous config <setting> <value>` | Configure (idle, interval, max) |

### Skills

| Command | Description |
|---|---|
| `!bonzai skill list [category]` | List available skills |
| `!bonzai skill info <id>` | Show skill details and pricing |
| `!bonzai skill run <id> [inputs]` | Execute a skill |

### General

| Command | Description |
|---|---|
| `!bonzai help` | Show full command reference |

---

## How Inference Routing Applies

When a user sends `!bonzai generate image a sunset` from WhatsApp:

1. OpenClaw receives the webhook on port 18789
2. The handler calls `executeInference('image_turbo', params)`
3. `executeInference` calls `window.electronAPI.inferenceRequest('image_turbo', params)`
4. The unified `inference-request` handler in main.js checks `p2p.networkMode`:
   - **Local/Provider**: routes to `http://127.0.0.1:65000/image/turbo`
   - **Consumer**: picks a random selected provider and sends via P2P
5. Result is returned through the webhook response to the user's chat

The same applies to LLM, audio, video, music, and vision requests. If pipeline parallelism is enabled and the request is LLM, it goes through the pipeline orchestrator with RPC shards.

---

## Session Management

Each messaging channel maintains its own session:

- **Conversation history**: stored per channel ID
- **Selected companion**: per channel
- **Selected scenario**: per channel
- **Generation settings**: per channel

Sessions persist across restarts (stored in Electron Store).

---

## Companion Presence

When a companion is selected for a channel, it responds to @mentions and regular messages using the companion's configured persona. The companion's personality (Big 5 traits, backstory, content level) shapes response style.

Companions can also:
- Post autonomously when autonomous mode is enabled
- Moderate incoming prompts
- Respond to generation results with contextual commentary

---

## Troubleshooting

### "No model session" (503)

The LLM model isn't loaded. Either:
- Load a model: `!bonzai model llama_3_1_8b`
- Or switch to consumer mode with a provider that has models loaded

### Generation returns nothing

Check that the Flask server is running (port 65000). In the desktop app, any generative tab will show if the server is responsive.

### Webhook not received

Verify OpenClaw gateway is running on port 18789. Check the desktop app console for `[OpenClaw]` log messages.

### Network mode shows "local" but you expected remote

Network mode is set exclusively in the BonzAI desktop application. Chat commands cannot change it. Open P2P Network settings and verify your mode and selected providers.
