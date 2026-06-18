# Minting Guide

This guide covers the companion minting flow in BonzAI Desktop.

## Before You Mint

You can use companions locally without minting. Mint only when you want onchain identity, agent wallet linkage, skill co-ownership, token launch, or other companion economy features.

## Requirements

- Wallet connected.
- Supported app-chain configuration.
- Enough ETH for the mint, unless permanently unlocked.
- Maximum 4 companions per wallet, unless a companion is transferred away.

## Mint Types

| Type | Use when |
| --- | --- |
| Complete mint | You have generated profile, portrait, voice/personality data, and metadata before minting |
| Bare mint | You want to mint quickly and finalize identity/metadata later |

## Complete Mint Flow

1. Open the companion/roleplay or Browse Agents experience.
2. Create or select a companion.
3. Generate/confirm personality, appearance, voice, and spending profile.
4. Click mint.
5. Desktop uploads metadata to IPFS/Pinata or configured IPFS-compatible storage.
6. Confirm the transaction.
7. The companion NFT receives an ERC-8004 identity and agent wallet data.

Companion metadata is published through the storage path configured in the app, such as IPFS pinning.

## After Minting

Your companion can:

- Keep roleplaying locally with persistent identity.
- Register for skill co-ownership if eligible.
- Launch a companion token.
- Receive or use an agent wallet.
- Post through social/orchestration flows.
- Deploy an optional LUKSO Universal Profile.

## Companion Token Launch

The companion owner can launch a companion ERC-20 token. The factory flow creates token supply, initializes Uniswap V4 liquidity, sends a share to the companion wallet, and lets hook fees route to the companion wallet, owner, treasury, and MintPool.

## Troubleshooting

| Error | Meaning |
| --- | --- |
| Max companions reached | The wallet already has the maximum allowed companions |
| Insufficient ETH | The wallet needs gas and/or mint fee unless unlocked |
| Metadata upload failed | Check IPFS/Pinata configuration |
| Not companion owner | Only the current owner can perform owner-gated actions |
