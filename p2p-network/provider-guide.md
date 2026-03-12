# Provider Guide

Share your GPU with the BonzAI network and earn ETH or USDC for processing inference requests.

## Registration

### Via the App

1. Open **Network Settings** in BonzAI
2. Switch to **Provider** mode
3. Select the pipelines you want to offer (LLM, Image, Audio, etc.)
4. Set your price per 1,000 tokens
5. Choose your payment currency (ETH or USDC)
6. Click **Register** — this sends a transaction to the BonzaiProviderRegistry on Base

### On-Chain Details

Registration calls `BonzaiProviderRegistry.register()` with:

| Parameter | Description |
|-----------|-------------|
| `peerId` | Your libp2p peer ID (auto-generated) |
| `multiaddrs` | Your libp2p multiaddresses for dialing |
| `pipelines` | Array of pipeline IDs you support (0-10) |
| `pricePerToken` | Price per 1,000 tokens in wei |
| `isRelay` | Whether you also act as a relay node |

Registration requires a minimum ETH stake (sent as `msg.value`).

## Provider Lifecycle

| Action | Function | Description |
|--------|----------|-------------|
| Register | `register()` | Join the network, set capabilities |
| Heartbeat | `heartbeat()` | Update `lastSeenAt` timestamp |
| Update | `updateProvider()` | Change pipelines, pricing, or peerId |
| Deactivate | `deactivate()` | Stop accepting jobs |
| Activate | `activate()` | Resume accepting jobs |
| Withdraw Stake | `withdrawStake()` | Recover staked ETH (must deactivate first) |

## Earning Revenue

When you process an inference request:

1. Consumer pays via BonzaiPayment (ETH or USDC)
2. **2.5% platform fee** is sent to treasury
3. **97.5%** is credited to your pending withdrawals
4. Your `totalEarnings` and `completedJobs` are updated in the registry

### Withdrawing Earnings

- **ETH earnings**: Call `withdrawETHEarnings()` on BonzaiPayment
- **USDC earnings**: Call `withdrawEarnings()` on BonzaiPayment

Both can be done via the Network Settings UI or directly on the contract.

## Pipeline Categories

When registering, specify which pipelines you support using their numeric IDs:

```
0: LLM (all 21 models)
1: IMAGE_TURBO        6: AUDIO_TURBO
2: IMAGE_QUALITY      7: AUDIO_QUALITY
3: IMAGE_STANDARD     8: MUSIC
4: IMAGE_ADVANCED     9: VIDEO_FAST
                     10: VISION
```

## Hardware Recommendations

| Pipeline | Minimum VRAM | Recommended |
|----------|-------------|-------------|
| LLM (small models) | 4 GB | 8 GB |
| LLM (large models) | 16 GB | 24 GB |
| Image | 6 GB | 12 GB |
| Audio | 2 GB | 4 GB |
| Video | 10 GB | 16 GB |
| Vision | 6 GB | 8 GB |
