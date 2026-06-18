# Scenario Map

This section explains BonzAI through user scenarios. The goal is to make the system understandable from the user's point of view: what they click, what runs locally, what gets stored, what goes onchain, and where rewards can come from.

## Common Paths

| User goal | Product path | Onchain path |
| --- | --- | --- |
| Chat privately | BonzAI Web, BonzAI+, or Desktop text generation | None required |
| Capture material from the web | BonzAI+ Dataset mode | None required unless publishing |
| Build a training dataset | BonzAI+ export -> Desktop Contribution Studio | Optional contribution/dataset registry publish |
| Generate images/audio/video | BonzAI Desktop or BonzAI+ Imagine | None required unless minting |
| Mint generated content | Desktop -> Content NFT flow | Level/unlock check, IPFS metadata, mint fee split |
| Create a companion | Desktop Roleplay/Browse Agents | Companion NFT mint, ERC-8004 metadata |
| Launch a companion token | Desktop companion card | Companion token factory + Uniswap V4 hook revenue |
| Co-own skill revenue | Desktop skill ownership flows | Skill registry + skill ownership contract |
| Earn as a provider | Desktop Provider mode | Provider registry + service-time reward claim |

## What Stays Local

By default, prompts, generated outputs, datasets, transcript entries, and contribution drafts stay on the user's device. They only leave the device when the user exports, shares, publishes, mints, routes through P2P, or explicitly uploads metadata/assets to IPFS.

## What Goes Onchain

The blockchain stores compact economic records: ownership, token balances, minting rights, fee routes, pool accounting, registry hashes, and claimable rewards. Large files do not belong onchain.

## What Goes To IPFS

When a published/minted asset needs off-device metadata or media, BonzAI uses IPFS-compatible storage through Pinata or configured app services. BonzAI does not use Irys.
