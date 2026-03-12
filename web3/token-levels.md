# BONZAI Token & Levels

## Token

**BONZAI** is an ERC-20 token deployed on three networks:

| Network | Address |
|---------|---------|
| Ethereum | [`0xDdA9Ff241C7160be8295EF9Eca2e782361467666`](https://etherscan.io/token/0xDdA9Ff241C7160be8295EF9Eca2e782361467666) |
| Arbitrum | [`0x0a84edf70f30325151631ce7a61307d1f4d619a3`](https://arbiscan.io/token/0x0a84edf70f30325151631ce7a61307d1f4d619a3) |
| Base | [`0xc4d137def384ee0f8857887f5950669ba04984ec`](https://basescan.org/token/0xc4d137def384ee0f8857887f5950669ba04984ec) |

## Level System

**All AI generation is free (LVL0).** Levels only gate **minting** content as NFTs and co-owning revenue pools.

| Level | BONZAI Required | Minting Rights | Revenue Pool |
|-------|----------------|----------------|--------------|
| **LVL1** | 1,000 | Text NFTs | Text pool |
| **LVL2** | 5,000 | Audio NFTs | Audio pool |
| **LVL3** | 10,000 | Image NFTs | Image pool |
| **LVL4** | 25,000 | Video NFTs | Video pool |
| **LVL5** | 33,000 | 3D NFTs | 3D pool |
| **LVL6** | 50,000 | Training NFTs, ERC-20 token issuance | Training pool |

### How Levels Work

- Hold the required BONZAI tokens in your connected wallet (on any supported chain)
- Levels are checked in real-time — no staking or locking required
- Higher levels include all lower-level permissions (LVL3 can mint text + audio + images)

### Alternative: One-Time Unlock

Pay **1 ETH** via the BonzaiUnlock contract on Base to unlock **all 6 levels permanently**.

- Contract: [`0xeDadE2f8fa659817E000b887f3d8222c4AC687B8`](https://basescan.org/address/0xeDadE2f8fa659817E000b887f3d8222c4AC687B8)
- Proceeds split: 50% Foundation / 50% Liquidity
- One-time payment — no recurring fees

## MintPool Revenue

Each level corresponds to an epoch-based revenue pool managed by the BonzaiMintPool contract:

- **Weekly epochs** (604,800 seconds)
- BONZAI holders register per epoch with their token balance
- After an epoch ends, registered holders claim a proportional share of pool revenue
- Revenue comes from content mint fees (20%) and Uniswap V4 hook fees
- **256-block gap enforcement** prevents flash loan attacks

### Pool Thresholds

| Pool | BONZAI Required |
|------|----------------|
| Text (0) | 1,000 |
| Audio (1) | 5,000 |
| Image (2) | 10,000 |
| Video (3) | 25,000 |
| 3D (4) | 33,000 |
| Training (5) | 50,000 |

Unclaimed funds are sweepable by the contract owner after N+2 epochs.

## Treasury

| Wallet | Purpose |
|--------|---------|
| `0x8Ff3b2e823b33BeE30e699bB1b6BBc8F622fEa89` | Foundation / Treasury |
| `0x4135d59f0BfF96560b7aD5cfCe81154AB1810B93` | Liquidity Management |
