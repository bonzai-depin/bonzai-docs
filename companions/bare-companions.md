# Bare Companions

Bare companions are a pre-reveal minting flow that lets you mint a companion NFT instantly without generating personality, portrait, or metadata first. You personalize the companion later through a guided setup wizard.

## Why Mint Bare?

- **Speed** — Mint in seconds, no AI generation needed
- **External minting** — Mint through the configured contract explorer, OpenClaw, or another dApp, then set up in BonzAI
- **Batch minting** — Secure multiple token IDs quickly, personalize each one later
- **Deferred decisions** — Lock in your spot now, decide on personality and appearance later

## How to Mint a Bare Companion

### Option A: Via OpenClaw / Hermes (Fastest)

Send a command through any connected channel (WhatsApp, Telegram, Discord, Mattermost):

```
!mint bare
!mint bare female
!mint bare male
```

The system mints immediately with placeholder metadata. You'll receive a confirmation with:
- Token ID
- Agent wallet address
- Transaction hash
- A link to bonzai.sh to complete the setup

### Option B: Via Contract Explorer

Call `mintCompanion()` on the configured `BonzaiCompanions` contract with:
- `agentURI`: any placeholder URI (e.g., `ipfs://pending`)
- `personalityHash`: `0x0`
- `spendingProfile`: `0`
- `gender`: `0` (neutral), `1` (female), or `2` (male)
- `agentWallet`: your own address (will be replaced during finalization)
- `value`: 0.25 ETH (free for unlocked users)

## What a Bare Companion Looks Like

In the **Browse Agents** tab under **My Companions**, bare companions appear with:
- A generic gray avatar icon (no portrait yet)
- An orange **"Needs Setup"** badge
- The text: "Minted but not configured. Click to set up."
- A prominent **"Set Up Companion"** button

## Finalizing: The 5-Step Setup Wizard

Click **"Set Up Companion"** to open the setup wizard. It walks you through five steps:

### Step 1: Identity

| Field | Required | Description |
|-------|----------|-------------|
| First Name | Yes | e.g., "Luna" |
| Family Name | Yes | e.g., "Starling" |
| Gender | Yes | Neutral, Female, or Male |
| Age | Yes | Must be 18+ |
| Short Bio | Yes | Brief description of your companion |

### Step 2: Personality

Configure the Big 5 (OCEAN) personality traits using five sliders (1-10 each):

| Trait | Description |
|-------|-------------|
| **Openness** | Curiosity, creativity, willingness to try new things |
| **Conscientiousness** | Discipline, organization, goal-oriented behavior |
| **Extraversion** | Sociability, energy, enthusiasm in interactions |
| **Agreeableness** | Cooperation, empathy, warmth toward others |
| **Neuroticism** | Emotional sensitivity, intensity of reactions |

You'll also fill in:
- **Background** — Backstory and history
- **Voice Style** — How they sound (e.g., "warm, sultry, professional")
- **First Message** — What they say when you first meet

### Step 3: Appearance

- **Physical description** — Hair, eyes, build, clothing, distinguishing features
- **Style** — Choose from: Romantic, Cyberpunk, Fantasy, Anime, Realistic, or Gothic

### Step 4: Portrait

A preview area shows the portrait. Click **"Generate Portrait"** to create one from your appearance description using the image pipeline (Z-Image Turbo, square 768x768). You can regenerate until satisfied.

### Step 5: Confirm

Review a read-only summary of everything you've entered:
- Name, gender, age
- Big 5 scores
- Appearance and style
- Portrait preview

A notice explains that finalization requires multiple on-chain transactions. Make sure you have enough native gas token on the configured app chain.

Click **"Confirm"** to begin finalization.

## Finalization Process

After confirming, BonzAI executes the following steps with a progress bar:

| Step | Action |
|------|--------|
| 1 | Verify NFT ownership |
| 2 | Generate spending profile from personality |
| 3 | Generate portrait (if not already done) |
| 4 | Upload portrait to IPFS |
| 5 | Build full ERC-8004 registration metadata |
| 6 | Upload metadata to IPFS |
| 7 | Set agent URI on-chain (`setAgentURI`) |
| 8 | Create agent wallet |
| 9 | Set agent wallet on-chain (`setAgentWallet`) |
| 10 | Set spending profile on-chain |
| 11 | Set personality hash on-chain |
| 12 | Set OASF traits via `setMetadataBatch()` |

Each on-chain step requires a wallet confirmation. Once complete, the wizard closes and your companion card updates with its portrait, name, and a blue **"Minted"** badge.

## After Finalization

Your companion is now fully set up and identical to one minted through the [complete minting flow](minting-guide.md). You can:

- Use them in **Roleplay** sessions
- **Launch a token** for them
- **Register for skill co-ownership**
- **Deploy a LUKSO Universal Profile**
- **Connect via OpenClaw** for multi-channel chat

## Detection

The app detects bare companions by checking:
- `metadata.bonzai.status === 'pending_setup'`
- `metadata.active === false` and name contains "Pending Setup"

Any companion matching these conditions shows the "Needs Setup" badge and setup wizard button.
