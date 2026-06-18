# BONZAI Token & Levels

BONZAI levels gate minting rights and economic participation. They do not gate ordinary AI generation.

## Token Addresses

| Network | BONZAI token |
| --- | --- |
| Ethereum | `0xDdA9Ff241C7160be8295EF9Eca2e782361467666` |
| Arbitrum | `0x0a84edf70f30325151631ce7a61307d1f4d619a3` |
| Base | `0xc4d137def384ee0f8857887f5950669ba04984ec` |

## Levels

| Level | BONZAI held | Unlocks |
| --- | ---: | --- |
| LVL1 | 1,000 | Text NFT minting, text pool eligibility |
| LVL2 | 5,000 | Audio NFT minting, audio pool eligibility |
| LVL3 | 10,000 | Image NFT minting, image pool eligibility |
| LVL4 | 25,000 | Video NFT minting, video pool eligibility |
| LVL5 | 33,000 | 3D NFT minting, 3D pool eligibility |
| LVL6 | 50,000 | Training NFT minting, model/fine-tune token issuance, training pool eligibility |

## Permanent Unlock

The unlock contract can grant all levels permanently through a one-time ETH payment. Where supported by the contracts, unlocked users:

- Mint content NFTs for free.
- Mint companion NFTs for free.
- Bypass level thresholds for minting rights.

Unlock proceeds route 50% to foundation/treasury and 50% to liquidity according to the configured contract.

## What Levels Do Not Do

Levels do not stop users from:

- Chatting.
- Generating images/audio/video locally.
- Using BonzAI+ Chat/Live/Imagine/Dataset modes.
- Importing or exporting local datasets.
- Running private local workflows.

## Pool Eligibility

Level thresholds matter for MintPool holder rewards. To claim a content-type pool, a user generally needs:

1. Enough BONZAI for that level.
2. Epoch registration.
3. Content-type activity recorded for that epoch.
4. Claim confirmation after the epoch.
5. The required block gap before final claim.

For the complete flow, see [Reward Structure & Epochs](reward-structure.md).
