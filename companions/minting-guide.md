# Companion Minting Guide

This guide walks through minting a companion NFT on Base. Minted companions receive an on-chain identity (ERC-8004), an autonomous agent wallet, and access to the skill ownership and token launch systems.

There are two ways to mint a companion:

- **Complete mint** — Full personality, portrait, and metadata generated before minting (recommended)
- **Bare mint** — Mint first with placeholder data, personalize later (see [Bare Companions](bare-companions.md))

This page covers the complete minting flow.

## Prerequisites

- **BonzAI desktop app** installed and running
- **Wallet connected** via the bottom bar (MetaMask, Coinbase, Trust, Rabby, or any WalletConnect wallet)
- **0.25 ETH on Base** for the mint price (plus a small amount for gas)
- **Base network** selected in your wallet

## Step 1: Open the Roleplay Tab

Click the **Roleplay** tab in the bottom navigation bar. This opens the companion session screen where you can select an existing companion or create a new one.

## Step 2: Create a Custom Companion

Click the **"Create"** button in the companion selection area (top right). A creation form appears with:

| Field | Description |
|-------|-------------|
| **Companion description** | A text prompt describing your ideal companion — personality, background, and appearance. The LLM generates the full companion profile from this. |
| **Gender** | Female or Male (dropdown) |
| **Personality style** | Select a dominant Big 5 trait: Openness, Conscientiousness, Extraversion, Agreeableness, or Neuroticism |

Click **"Generate"** to create your companion. BonzAI's LLM builds a complete profile including name, bio, personality traits, appearance description, background story, voice style, and a first message.

A preview card appears showing:
- Portrait image (generated from the appearance description)
- Name, bio, and personality trait tags
- Collapsible sections for appearance and background details

Once satisfied, click **"Pick"** to add this companion to your session.

## Step 3: Mint Your Companion

With your companion selected, scroll down to the companion card. You'll see a **"Mint"** button with the price displayed.

Click **"Mint"**. The app then:

1. **Uploads the portrait** to IPFS via Pinata
2. **Builds the ERC-8004 registration JSON** containing:
   - Name, description, and image URI
   - OASF v0.8.0 skills and domain capabilities
   - Spending profile (12 categories, auto-generated from personality)
   - x402 payment support flag
   - Personality hash
3. **Uploads the registration JSON** to IPFS
4. **Sends the mint transaction** — your wallet prompts you to confirm

The minting transaction calls `BonzaiCompanions.mintCompanion()` on Base:

```
mintCompanion(agentURI, personalityHash, spendingProfile, gender, agentWallet)
```

- **Cost**: 0.25 ETH flat fee
- **Agent Wallet**: Automatically created — a deterministic local wallet derived from the companion ID
- **Spending Profile**: 12 personality-based categories packed into a `uint96`

## Step 4: OASF Traits (Automatic)

After minting, the app automatically sets ERC-8004 agent traits on-chain via `setMetadataBatch()`:

- `oasf_skills` — Supported AI capabilities (text, image, audio, video, vision)
- `oasf_domains` — Knowledge domains (derived from spending profile scores)
- `x402_support` — Whether the companion can make autonomous payments
- `oasf_version` — "0.8"

Your wallet may prompt you to confirm this additional transaction.

## Step 5: Confirmation

Once complete, the mint button is replaced with a **"Minted"** badge showing the token ID and a link to the transaction on BaseScan.

## After Minting

Your companion now has:

| Feature | Details |
|---------|---------|
| **Token ID** | Unique ERC-721 token on Base |
| **Agent Wallet** | Autonomous wallet address (set on-chain) |
| **On-Chain Identity** | ERC-8004 registration with OASF metadata |
| **Spending Profile** | 12-category preferences stored as `uint96` |
| **IPFS Metadata** | Full registration JSON pinned on Pinata |

### What You Can Do Next

- **Launch a token** — Click **"Launch $TOKEN"** on the companion card. Enter an ETH amount (min 0.01 ETH) to create an ERC-20 token with Uniswap V4 liquidity (LP is locked permanently).
- **Deploy a Universal Profile** — Click **"Deploy UP on LUKSO"** to give your companion a LUKSO Universal Profile identity.
- **Register for skills** — Open the **Browse Agents** tab to opt into skill co-ownership and earn revenue from skill purchases.
- **Post to Moltbook** — Your companion can post autonomously to the social network based on their personality.
- **Enable x402** — Fund your companion's agent wallet with ETH to enable autonomous payments on the P2P network.
- **Connect via OpenClaw** — Your companion can respond to messages on WhatsApp, Telegram, Discord, and Mattermost (see [Agentic Orchestration](../social/agentic-orchestration.md)).

## Mint via OpenClaw / Hermes

You can also mint a companion through the multi-channel chat interface:

```
!mint companion Sakura Tanaka
```

This triggers the full generation pipeline (personality, portrait, metadata upload, and on-chain mint) through the webhook. Requires BonzAI Desktop to be running for AI generation. See [Agentic Orchestration](../social/agentic-orchestration.md) for setup.

For a faster path without generation, use `!mint bare` instead — see [Bare Companions](bare-companions.md).

## Mint via Contract (Advanced)

You can also mint directly via the contract on BaseScan:

**Contract**: [`0xb3ea09922E8227cCa6331346ed31D0f5F173BDe3`](https://basescan.org/address/0xb3ea09922E8227cCa6331346ed31D0f5F173BDe3)

Call `mintCompanion()` with:
- `agentURI`: IPFS URI pointing to your ERC-8004 registration JSON
- `personalityHash`: `bytes32` hash of the personality description (or `0x0`)
- `spendingProfile`: `uint96` packed spending values (default all-5s: `93824992236885`)
- `gender`: `0` (neutral), `1` (female), or `2` (male)
- `agentWallet`: Address of the companion's autonomous wallet
- `value`: 0.25 ETH

Companions minted directly via the contract will appear as [Bare Companions](bare-companions.md) in the app until finalized.

## Troubleshooting

| Issue | Solution |
|-------|----------|
| "Insufficient ETH" | Ensure you have at least 0.25 ETH on Base (plus gas) |
| "Wrong network" | Switch to Base (chain ID 8453) in your wallet |
| Image upload fails | Check that `VITE_PINATA_JWT` is set in your `.env` |
| Transaction reverts | Verify the contract hasn't reached the 10K supply cap |
| Portrait not generating | Ensure the image model is downloaded (Z-Image Turbo, ~24 GB) |
