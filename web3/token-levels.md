# Levels & Utility

BonzAI currently contains two related level systems during the v4 transition. They must not be confused.

## Legacy holding/mint levels

These existing application thresholds gate content mint categories, not local generation:

| Level | Wallet balance | Mint category |
| ---: | ---: | --- |
| 1 | 1,000 | Text |
| 2 | 5,000 | Audio |
| 3 | 10,000 | Image |
| 4 | 25,000 | Video |
| 5 | 33,000 | 3D |
| 6 | 50,000 | Training/model issuance |

The legacy one-time unlock may bypass compatible mint-level checks where deployed. It does not replace staking utility.

## v4 staking tiers

The deployment script currently initializes these staking thresholds:

| Tier | Staked `$BONZAI` |
| ---: | ---: |
| 1 | 1,000 |
| 2 | 5,000 |
| 3 | 10,000 |
| 4 | 25,000 |
| 5 | 50,000 |
| 6 | 100,000 |

Contract ownership can update thresholds. The deployed vault is the source of truth.

## Token addresses

| Network | `$BONZAI` |
| --- | --- |
| Ethereum | `0xDdA9Ff241C7160be8295EF9Eca2e782361467666` |
| Arbitrum | `0x0a84edf70f30325151631ce7a61307d1f4d619a3` |
| Base | `0xc4d137def384ee0f8857887f5950669ba04984ec` |

Always use the address shown by an official BonzAI source and verify the selected network.
