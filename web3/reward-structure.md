# Reward Structure & Epochs

This page explains how BonzAI rewards move through the protocol. It covers content mint pools, provider rewards, companion revenue, skill co-ownership, hook fees, royalties, and unclaimed funds.

## Main Reward Channels

| Channel | Who can earn | Source |
| --- | --- | --- |
| Holder MintPool rewards | BONZAI holders with level/activity eligibility | Holder side of MintPool deposits |
| Provider rewards | Registered/eligible providers with recorded service time | Provider side of MintPool deposits |
| Content royalties | Content creators and configured royalty routes | Secondary sales through ERC-2981/royalty splitter |
| Companion token hook fees | Companion wallet, companion NFT owner, treasury, MintPool | Uniswap V4 swaps |
| Fine-tune/model token hook fees | Model creator, treasury, MintPool | Uniswap V4 swaps |
| Skill co-ownership | Eligible companion co-owners | Skill purchases/executions |
| Future contribution rewards | Dataset/model/evaluation contributors | Contribution registry and revenue routes |

## Content Mint Fee Flow

When a user mints a content NFT:

```text
mint fee
-> 80% treasury
-> 20% matching MintPool content bucket
```

The MintPool bucket deposit is split into:

```text
holder side + provider side
```

The default split is 50% holder side and 50% provider side, but the contract configuration is the source of truth.

## MintPool Buckets

There are six content buckets:

| Pool index | Content type | Level |
| ---: | --- | --- |
| 0 | Text | LVL1 |
| 1 | Audio | LVL2 |
| 2 | Image | LVL3 |
| 3 | Video | LVL4 |
| 4 | 3D | LVL5 |
| 5 | Training | LVL6 |

## Holder Reward Flow

A BONZAI holder claim is not automatic. The typical flow is:

1. The user holds enough BONZAI for the pool threshold.
2. The user registers for the epoch.
3. The user has matching content-type activity recorded in that epoch.
4. The epoch ends and is finalized.
5. The user confirms the claim.
6. The user waits the required confirmation gap, currently 256 blocks.
7. The user claims their proportional reward.

The reward is based on the user's time-weighted eligible BONZAI balance relative to all eligible registered holders in that pool.

## Provider Reward Flow

Provider rewards use the provider side of MintPool deposits.

1. A user runs Desktop in Provider mode.
2. The provider registers/advertises supported pipelines where the registry path is used.
3. The provider serves inference.
4. Service time is recorded for the epoch.
5. The epoch finalizes.
6. The provider claims their share.

Formula:

```text
provider reward = provider seconds / total provider seconds * provider-side pool amount
```

Provider claims require the configured BONZAI threshold at record/claim time. Current service-time reward docs should be treated as the default provider economy. Older direct ETH/USDC x402 rails may still exist as optional or legacy infrastructure, but they are not the main reward explanation.

## Epoch Duration

Epoch duration is a contract deployment parameter. The intended production cadence is weekly, while tests may use a longer duration. Always treat the deployed contract's `epochDuration` as the source of truth.

## Unclaimed Funds

After an epoch is finalized, unclaimed amounts can be handled by owner-only maintenance functions:

- **Sweep**: move remaining unclaimed holder/provider funds to treasury.
- **Recirculate**: roll remaining holder/provider funds into the current epoch.

Docs and UI should make clear whether a claim window is still open before implying funds are permanently lost.

## Companion Revenue

Companion economics has multiple reward paths:

### Companion Minting

Companion NFTs are ERC-721 + ERC-8004 identities. Minting may cost ETH unless the user has permanent unlock, in which case companion minting can be free where supported.

### Companion Token Hook Fees

A companion owner can launch a companion ERC-20 token. The launch flow sends most supply to Uniswap V4 liquidity and a smaller share to the companion wallet. Swap hook fees route:

| Recipient | Share |
| --- | ---: |
| Companion agent wallet | 40% |
| Companion NFT owner | 40% |
| Treasury | 10% |
| MintPool | 10% |

The MintPool share is spread across the six content buckets according to hook logic.

### Skill Co-Ownership

Companions can register as skill co-owners. Skill revenue routes:

| Recipient | Share |
| --- | ---: |
| Skill co-owner distribution | 80% |
| Treasury | 20% |

Within the co-owner distribution, weights are:

```text
BONZAI balance of companion wallet * spending profile score
```

The companion must remain eligible. If a companion NFT is transferred and the registration no longer matches the owner/attestation requirements, the old registration can be skipped during distribution.

## Fine-Tune / Model Token Revenue

Fine-tune/model tokens use the same Uniswap V4 hook system with a different split:

| Recipient | Share |
| --- | ---: |
| Model/fine-tune creator | 80% |
| Treasury | 10% |
| MintPool | 10% |

The MintPool share is spread across the six content buckets.

## Contribution Rewards

Contribution registries extend reward routing beyond the initial mint/token systems. The intended future flow is:

1. A contribution pack records useful dataset/model/evaluation work.
2. Desktop imports it into a local ledger.
3. The user publishes a hash/license/attribution record when registries are configured.
4. Revenue from downstream use can route back to contributors.

This is the core of Proof-of-Contribution AI.
