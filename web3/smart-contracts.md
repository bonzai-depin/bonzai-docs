# Smart Contracts

All protocol contracts are deployed on **Base** (chain ID 8453).

## MVP Contracts

| Contract | Address | Purpose |
|----------|---------|---------|
| BonzaiMintPool | [`0xB9423Ef7cedAAC87419511Fa1E24DE65C19c7CD2`](https://basescan.org/address/0xB9423Ef7cedAAC87419511Fa1E24DE65C19c7CD2) | Epoch-based revenue pools for LVL holders |
| BonzaiContent | [`0xdcCF8d2A328F87eDC304898a35F9798ad5Bf87e9`](https://basescan.org/address/0xdcCF8d2A328F87eDC304898a35F9798ad5Bf87e9) | ERC-721 content NFT with fee splitting |
| BonzaiRoyaltySplitter | [`0x5B63AD58034D7396e7024F4Bebf8E5D86D668399`](https://basescan.org/address/0x5B63AD58034D7396e7024F4Bebf8E5D86D668399) | Secondary royalty distribution |
| BonzaiCompanions | [`0xb3ea09922E8227cCa6331346ed31D0f5F173BDe3`](https://basescan.org/address/0xb3ea09922E8227cCa6331346ed31D0f5F173BDe3) | ERC-721 + ERC-8004 companion NFT |
| BonzaiUniswapHook | See config | V4 afterSwap hook (1% fee) |
| CompanionTokenFactory | [`0xdD6Ba1f369C38A4D3ea02e81c7400B36A84E6099`](https://basescan.org/address/0xdD6Ba1f369C38A4D3ea02e81c7400B36A84E6099) | Atomic companion ERC-20 + V4 LP |
| FineTuneTokenFactory | [`0x54Ee513a7a6809c109408EA20dA9E7e424A6e36c`](https://basescan.org/address/0x54Ee513a7a6809c109408EA20dA9E7e424A6e36c) | Atomic model ERC-20 + V4 LP |
| BonzaiUnlock | [`0xeDadE2f8fa659817E000b887f3d8222c4AC687B8`](https://basescan.org/address/0xeDadE2f8fa659817E000b887f3d8222c4AC687B8) | 1 ETH all-level unlock |

## P2P Network Contracts

| Contract | Status | Purpose |
|----------|--------|---------|
| BonzaiProviderRegistry | Pending deployment | P2P provider registration and staking |
| BonzaiPayment | Pending deployment | ETH/USDC payment processing with EIP-712 |

## Cross-Contract Wiring

```
Content  → MintPool, RoyaltySplitter
MintPool → Content, RoyaltySplitter, FeeHook
Hook     → CompanionFactory (authorized), FineTuneFactory (authorized)
CompanionFactory → Companions (NFT ownership check)
FineTuneFactory  → Content (NFT ownership check)
Payment  ↔ ProviderRegistry (bidirectional)
```

## Key Parameters

| Parameter | Value |
|-----------|-------|
| Companion mint price | 0.25 ETH |
| Companion max supply | 10,000 |
| Content mint fee | 0.0025 ETH |
| Content royalties (ERC-2981) | 7.5% |
| Unlock price | 1 ETH |
| MintPool epoch duration | 7 days |
| Flash loan protection gap | 256 blocks |
| Hook swap fee | 1% |
| P2P platform fee | 2.5% |

## Solidity Version

All contracts compile with Solidity `0.8.20`, optimizer enabled (200 runs, viaIR).

## Uniswap V4 Addresses (Base)

| Component | Address |
|-----------|---------|
| PoolManager | `0x498581ff718922c3f8e6a244956af099b2652b2b` |
| PositionManager | `0x7c5f5a4bbd8fd63184577525326123b519429bdc` |
| Permit2 | `0x000000000022D473030F116dDEE9F6B43aC78BA3` |
