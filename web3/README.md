# Web3 & Tokenomics

BonzAI is a multi-chain application with smart contracts deployed across Ethereum, Arbitrum, Base, and LUKSO. The protocol is built around the BONZAI ERC-20 token, which gates NFT minting and revenue pool access.

## Supported Networks

| Network | Chain ID | Role |
|---------|----------|------|
| **Ethereum** | 1 | BONZAI token (primary) |
| **Arbitrum** | 42161 | BONZAI token (L2) |
| **Base** | 8453 | Protocol contracts, companion NFTs, content NFTs, Uniswap V4 |
| **LUKSO** | 42 | LSP8 content NFTs, Universal Profiles |

## Core Protocol (Base)

Base is the primary chain for all protocol operations:

- **8 MVP contracts** deployed and wired
- **Uniswap V4** integration with custom hooks
- **Companion NFTs** (ERC-8004)
- **Content NFTs** (ERC-721)
- **MintPool** revenue distribution
- **Token factories** for companions and fine-tuned models

## Key Concepts

- [BONZAI Token & Levels](token-levels.md) — How token holdings unlock minting tiers
- [Content NFTs](content-nfts.md) — Minting AI-generated content on-chain
- [Smart Contracts](smart-contracts.md) — Full contract reference
- [Uniswap V4 Hooks](uniswap-hooks.md) — Custom swap fee distribution
