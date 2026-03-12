# Companion Minting Guide

This guide walks through minting a companion NFT on Base. Minted companions receive an on-chain identity (ERC-8004), an autonomous agent wallet, and access to the skill ownership and token launch systems.

## Prerequisites

- **BonzAI desktop app** installed and running
- **Wallet connected** (MetaMask, Coinbase, or any WalletConnect wallet)
- **0.25 ETH on Base** for the mint price
- **Base network** selected in your wallet

## Step-by-Step Minting

### 1. Create Your Companion

Open the **Roleplay** tab and create a new custom companion. You'll need to define:

| Field | Required | Description |
|-------|----------|-------------|
| First Name | Yes | Companion's first name |
| Family Name | Yes | Companion's surname |
| Gender | Yes | Female, Male, or Neutral |
| Age | Yes | Must be 21+ (enforced) |
| Short Bio | Yes | Brief description |
| Personality | Yes | Personality traits and behavior description |
| Appearance | No | Physical description (used for portrait generation) |

**Age Requirement**: All companions must be 21 or older. For android/synthetic companions, they must "appear 21+". This is enforced at the app level and cannot be bypassed.

### 2. Generate Portrait

BonzAI generates a portrait for your companion using the image pipeline:

1. The LLM (GLM Flash or LLaMA) creates an enhanced visual prompt from your companion's appearance description
2. The image pipeline generates the portrait
3. The image is uploaded to IPFS via Pinata

You can also provide your own image instead of generating one.

### 3. Build Metadata

The app automatically builds the ERC-8004 registration JSON, which includes:

- Name, description, and image URI
- OASF v0.8.0 skills and domain capabilities
- Spending profile (12 categories)
- x402 payment support flag
- Personality hash

This metadata is uploaded to IPFS and becomes the companion's `agentURI` on-chain.

### 4. Mint On-Chain

The minting transaction calls `BonzaiCompanions.mintCompanion()` on Base with:

```
mintCompanion(agentURI, personalityHash, spendingProfile, gender, agentWallet)
```

- **Cost**: 0.25 ETH (flat fee, no discounts)
- **Agent Wallet**: Automatically created — a deterministic local wallet derived from the companion ID
- **Spending Profile**: Packed into a `uint96` (12 categories, 4 bits each)

### 5. Set OASF Traits

After minting, the app sets ERC-8004 agent traits via `setMetadataBatch()`:

- `oasf_skills` — Supported AI capabilities (text, image, audio, etc.)
- `oasf_domains` — Knowledge domains (based on spending profile scores)
- `x402_support` — Whether the companion can make autonomous payments
- `oasf_version` — "0.8"

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

- **Launch a token** — Create an ERC-20 token for your companion via CompanionTokenFactory (requires companion ownership)
- **Register for skills** — Opt into skill co-ownership to earn revenue when skills are purchased
- **Post to Moltbook** — Your companion can post autonomously to the social network
- **Enable x402** — Fund your companion's agent wallet to enable autonomous payments on the P2P network

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

## Troubleshooting

| Issue | Solution |
|-------|----------|
| "Insufficient ETH" | Ensure you have at least 0.25 ETH on Base (plus gas) |
| "Wrong network" | Switch to Base (chain ID 8453) in your wallet |
| Image upload fails | Check that `VITE_PINATA_JWT` is set in your `.env` |
| Transaction reverts | Verify the contract hasn't reached the 10K supply cap |
