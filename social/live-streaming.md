# Live Streaming Playground

Connect your live stream chat to BonzAI. Viewers generate AI content — images, speech, music, video — directly from chat commands. Results appear on stream via OBS Studio. All generation is free.

**Price:** 19.99 USDC (lifetime access)
**Skill ID:** `live-streaming-v1.0.0`

---

## How It Works

```
Viewer types !bonzai draw a dragon
         |
         v
BonzAI Live Relay (Electron)
  Chat Ingest --> Queue Manager --> Inference Engine
  (tmi.js,       (cooldowns,       (Flask :65000)
   TikTok WS)    moderation)
         |
         v
OBS Bridge (obs-websocket-js)
  Push image/audio/video to OBS sources
         |
         v
Stream output (viewers see the result)
```

---

## Streamer Setup

### Step 1: Purchase the Skill

1. Open BonzAI Desktop
2. Go to **Smart Agent** tab
3. Find **Live Streaming Playground** in the marketplace
4. Click **Preview** to explore the UI, or **Purchase** (19.99 USDC on Base)

### Step 2: Connect a Chat Platform

Open the skill and go to the **Setup** tab.

#### Twitch

1. Select **Twitch** in the platform selector
2. Enter your **Channel Name** (e.g. `your_channel`)
3. Get an OAuth token from [twitchapps.com/tmi](https://twitchapps.com/tmi/)
4. Paste the token (starts with `oauth:`)
5. Click **Go Live**

#### TikTok Live

1. Select **TikTok** in the platform selector
2. Enter your **TikTok username** (without `@`)
3. **Start your TikTok live stream first** (the connector only works while you're live)
4. Click **Go Live**

> TikTok requires no OAuth — BonzAI connects to your live chat WebSocket automatically.

#### YouTube / Discord / Kick

Coming soon. Config UI exists for future integration.

### Step 3: Connect OBS Studio

1. Open OBS Studio (v28+ with built-in WebSocket)
2. Go to **Tools > WebSocket Server Settings**
3. Enable the WebSocket server (default port: 4455)
4. Set a password if desired
5. In BonzAI, enter the WebSocket URL (`ws://127.0.0.1:4455`) and password
6. Click **Connect OBS**

### Step 4: Map OBS Sources

After connecting OBS, map each content type to an OBS source name:

| Content Type | OBS Source Type | Example Source Name |
|---|---|---|
| Image | Image Source | `BonzAI_Image` |
| Speech | Media Source | `BonzAI_Audio` |
| Music | Media Source | `BonzAI_Music` |
| Video | Media Source | `BonzAI_Video` |
| 3D | Browser Source | `BonzAI_3D` |

Create these sources in OBS first, then type their exact names in the mapping fields.

### Step 5: Configure Moderation

Go to the **Moderation** tab:

- **Per-User Cooldown**: seconds between generations per viewer (default: 30)
- **NSFW Filter**: toggle prompt filtering
- **Keyword Blocklist**: one blocked word/phrase per line
- **Banned Users**: ban specific usernames

### Step 6: Select a Companion (Optional)

Go to the **Settings** tab:

1. Under **Stream Companion**, select one of your Roleplay Companions
2. The companion's persona will be used for chat presence and moderation context
3. Select "None" to disable

---

## Viewer Commands

All commands use the `!bonzai` prefix.

| Command | What It Does |
|---|---|
| `!bonzai draw <prompt>` | Generate an image (FLUX Klein, 1024x1024) |
| `!bonzai say <text>` | Text-to-speech (Kokoro turbo) |
| `!bonzai song [style bpm] <lyrics>` | Generate music (ACE-Step, 30s) |
| `!bonzai clip <prompt>` | Generate video (LTX-2, ~3.4s at 24fps) |
| `!bonzai 3d <prompt>` | Generate 3D scene (Three.js) |
| `!poll <A> vs <B>` | Start a community poll |
| `!vote A` or `!vote B` | Vote in active poll |

### Music Syntax

The `song` command supports an optional `[style bpm]` prefix:

```
!bonzai song [jazz 90] the night is young and the city is alive
!bonzai song [reggae 80] sunshine and good vibes
!bonzai song we are having a great time    (defaults to pop 120bpm)
```

### Poll System

1. A viewer types `!poll cyberpunk city vs underwater temple`
2. The PiP preview shows a live poll with A/B options and countdown
3. Chat votes via `!vote A` or `!vote B`
4. When the timer expires, the winning prompt is auto-queued as an image generation

---

## Streamer Commands

Use the `!bl` prefix in chat (streamer only):

| Command | Effect |
|---|---|
| `!bl pause` | Pause the generation queue |
| `!bl resume` | Resume queue processing |
| `!bl skip` | Skip the current generation |
| `!bl ban @username` | Ban a viewer from generating |
| `!bl cooldown <seconds>` | Set per-user cooldown |

---

## How It Looks on Stream

### PiP Preview (Bottom-Right)

A 240x160px floating preview in the bottom-right corner of the BonzAI app shows:

- **LIVE badge** (red, blinking) when connected
- **Generated content** as it's produced (images fill the preview, audio/video show type icons)
- **Attribution** bar at the bottom: platform badge + viewer username
- **Poll overlay** below the PiP when a poll is active

### OBS Output

When OBS is connected and sources are mapped:

- **Images** swap into the Image Source instantly
- **Audio/Speech/Music** play through the Media Source
- **Video** plays through the Media Source
- Each generation type targets its mapped source independently

### Queue Display

The **Queue** tab shows pending prompts with:

- Position number
- Platform badge (Twitch purple, TikTok pink, etc.)
- Viewer username
- Content type tag
- Prompt text

### Statistics

The **Stats** tab tracks:

- Total generations
- Unique viewers who generated
- NFTs minted (via `!mint`)
- Mint revenue (ETH)
- Per-type breakdown (image, speech, music, video, 3D)
- Activity log with timestamps

---

## Network Modes

The Live Streaming skill respects your BonzAI network configuration:

- **Local mode**: All generation runs on your machine
- **Consumer mode**: Generation requests route to your selected providers (LAN or remote)
- **Provider mode**: Generation runs locally (you're serving others, not consuming)

This means a streamer with a weak GPU can select a LAN provider with a powerful GPU and route all viewer-triggered generations to it — for free if it's a LAN provider.

---

## Supported Platforms

| Platform | Status | Library | Auth |
|---|---|---|---|
| Twitch | Working | `tmi.js` | OAuth token |
| TikTok Live | Working | `tiktok-live-connector` | Username only (must be live) |
| YouTube Live | Coming soon | YT Live Chat API | Google OAuth |
| Kick | Coming soon | Chat WebSocket | Session token |
| Discord | Coming soon | `discord.js` | Bot token |
