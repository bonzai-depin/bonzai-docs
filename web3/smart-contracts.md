# Smart Contracts

All protocol contracts are deployed on **Base** (chain ID 8453).

## Protocol Contracts (v3)

| Contract | Address | Purpose |
|----------|---------|---------|
| BonzaiMintPool | [`0x3a31aE7F6E03E095D5D68a4D6c7165Ba2b2E6D4c`](https://basescan.org/address/0x3a31aE7F6E03E095D5D68a4D6c7165Ba2b2E6D4c) | Epoch-based revenue pools (2-week epochs, threshold snapshots, unlocked users bypass thresholds) |
| BonzaiCollectibles | [`0x44f1675eBeB7f7A4Ac3E99E4A4652b34515F1F36`](https://basescan.org/address/0x44f1675eBeB7f7A4Ac3E99E4A4652b34515F1F36) | ERC-721 content NFT implementation (ERC-1167 clone per user) |
| BonzaiCollectiblesFactory | [`0xCF5d739674A9daf91Da83CF84eDE1456B7f17BC2`](https://basescan.org/address/0xCF5d739674A9daf91Da83CF84eDE1456B7f17BC2) | Factory deploying per-user collection clones |
| BonzaiRoyaltySplitter | [`0x798Bcae41E3A08B216D0Df6f03Be1e4eBEED9f24`](https://basescan.org/address/0x798Bcae41E3A08B216D0Df6f03Be1e4eBEED9f24) | Secondary royalty distribution (2/3 treasury, 1/3 pools weighted by activity) |
| BonzaiCompanions | [`0x0889B53F810aF1bFc83EFFD459E945a1a4D79c38`](https://basescan.org/address/0x0889B53F810aF1bFc83EFFD459E945a1a4D79c38) | ERC-721 + ERC-8004 companion NFT, 10K max supply |
| BonzaiUniswapHook | [`0x0d4B1d95ec00A6BC794B4bE18D1dF4136D524090`](https://basescan.org/address/0x0d4B1d95ec00A6BC794B4bE18D1dF4136D524090) | V4 afterSwap hook (1% fee capture) |
| CompanionTokenFactory | [`0x0cD90Ef3a38Ab8E845D3538Dc55EB9bd9C9e0477`](https://basescan.org/address/0x0cD90Ef3a38Ab8E845D3538Dc55EB9bd9C9e0477) | Atomic companion ERC-20 + V4 LP (96/4 split, LP locked) |
| FineTuneTokenFactory | [`0x9bd9621b8F77e501063b0ec8CD15e6f53bDc6B34`](https://basescan.org/address/0x9bd9621b8F77e501063b0ec8CD15e6f53bDc6B34) | Atomic model ERC-20 + V4 LP |
| BonzaiUnlock | [`0x7A33a9843C1740Ea73594fA2468Fb210a7fd7968`](https://basescan.org/address/0x7A33a9843C1740Ea73594fA2468Fb210a7fd7968) | 1 ETH all-level unlock (50/50 foundation/liquidity split) |

## Skill Economy Contracts

| Contract | Address | Purpose |
|----------|---------|---------|
| BonzaiSkillRegistry | [`0xeeB6B8A73B13141013416D74A327180905AFdF3F`](https://basescan.org/address/0xeeB6B8A73B13141013416D74A327180905AFdF3F) | Skill marketplace (80% co-owners, 20% platform, free for unlocked users) |
| BonzaiSkillOwnership | [`0xa1f80ABCe763De90eB873990C5841F7B1770383C`](https://basescan.org/address/0xa1f80ABCe763De90eB873990C5841F7B1770383C) | Companion co-ownership with weighted revenue distribution |

## P2P Inference Contracts

| Contract | Address | Purpose |
|----------|---------|---------|
| BonzaiProviderRegistry | [`0x683d0B11a2553E9D4B338935e2D935873439e8bB`](https://basescan.org/address/0x683d0B11a2553E9D4B338935e2D935873439e8bB) | Provider registration, staking, shard capabilities |
| BonzaiPayment | [`0x438A73FC0e0DA882BFdD007aF41415769Af33F1d`](https://basescan.org/address/0x438A73FC0e0DA882BFdD007aF41415769Af33F1d) | Single-provider ETH/USDC payments with EIP-712 (x402) |
| BonzaiPipelinePayment | [`0xB45D1D635192Aa223Ce28d9F3cC047A13D8850Bd`](https://basescan.org/address/0xB45D1D635192Aa223Ce28d9F3cC047A13D8850Bd) | Multi-payee atomic pipeline payments for private inference |

## Cross-Contract Wiring

```
Content  --> MintPool (20% of mint fees), RoyaltySplitter
MintPool --> CollectiblesFactory, RoyaltySplitter, FeeHook, CompanionNFT
Hook     --> CompanionFactory (authorized), FineTuneFactory (authorized)
CompanionFactory --> Companions (NFT ownership check)
FineTuneFactory  --> Collectibles (NFT ownership check)
SkillRegistry <--> SkillOwnership (bidirectional)
SkillOwnership --> USDC token
Payment <--> ProviderRegistry (bidirectional)
PipelinePayment --> ProviderRegistry
```

## Key Parameters

| Parameter | Value |
|-----------|-------|
| Companion mint price | 0.25 ETH (free for unlocked users) |
| Companion max supply | 10,000 |
| Companions per wallet | 4 max |
| Companion token supply split | 96% liquidity pool, 4% companion wallet |
| Content mint fees | 0.0005-0.005 ETH per type (free for unlocked) |
| Content fee split | 80% treasury, 20% MintPool |
| Content royalties (ERC-2981) | 7.5% |
| Royalty split | 2/3 treasury, 1/3 pools (weighted by activity) |
| Unlock price | 1 ETH (unlocks all levels permanently) |
| MintPool epoch duration | 2 weeks (1,209,600 seconds) |
| Flash loan protection | 256 blocks (~8.5 minutes on Base) |
| Hook swap fee | 1% |
| Companion hook fee split | 34% wallet, 33% owner, 33% LVL6 pool |
| FineTune hook fee split | 80% creator, 10% treasury, 10% LVL6 pool |
| Skill purchase split | 80% co-owners (weighted), 20% author |
| P2P platform fee | 2.5% |
| Pipeline max providers | 16 per session |

## Solidity Version

All contracts compile with Solidity `0.8.34`, optimizer enabled (200 runs, viaIR), EVM target `cancun`.

## Uniswap V4 Addresses (Base)

| Component | Address |
|-----------|---------|
| PoolManager | `0x498581ff718922c3f8e6a244956af099b2652b2b` |
| PositionManager | `0x7c5f5a4bbd8fd63184577525326123b519429bdc` |
| Permit2 | `0x000000000022D473030F116dDEE9F6B43aC78BA3` |

## Treasury Wallets

| Wallet | Address |
|--------|---------|
| Foundation / Treasury | `0x8Ff3b2e823b33BeE30e699bB1b6BBc8F622fEa89` |
| Liquidity | `0x4135d59f0BfF96560b7aD5cfCe81154AB1810B93` |
