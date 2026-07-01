# Smart Contracts

Contract addresses are release and network specific. The deployed address shown by the application and official deployment record is authoritative.

## v4 contribution economy

| Contract | Purpose |
| --- | --- |
| `BonzaiStakingVault` | `$BONZAI` stake, locks, attested contribution score, tiers, and utility weight |
| `BonzaiContributionScoreOracle` | Evidence-backed score attestations from authorized evaluators |
| `BonzaiRevenueRouter` | Immutable base contribution shares plus separate staking bonus |
| `BonzaiContributionRegistry` | General contribution identities and hashes |
| `BonzaiDatasetRegistry` | Dataset identity, licenses, and contributors |
| `BonzaiModelRegistry` | Model identity, provenance, validation, and routes |
| `BonzaiEvaluationRegistry` | Model/dataset evaluation records |
| `BonzaiJobEscrow` | Funded companion jobs, evidence, approval, and payout routing |

## Content and rewards

| Contract | Purpose |
| --- | --- |
| `BonzaiCollectibles` | Content NFTs, mint fees, royalties, and transfer rules |
| `BonzaiRoyaltySplitter` | Secondary royalty distribution |
| `BonzaiMintPool` | Six legacy/transitional weekly reward pools |
| `BonzaiUnlock` | Compatible one-time legacy mint-level unlock |

## Companions and models

| Contract | Purpose |
| --- | --- |
| `BonzaiCompanions` | Companion NFT and ERC-8004 identity; atomic token launch when factory is configured |
| `CompanionTokenFactory` | Fixed-supply companion token and permanent Uniswap V4 liquidity |
| `FineTuneTokenFactory` | Validated fine-tuned/abliterated model token and liquidity |
| `BonzaiUniswapHook` | One-percent contribution routing from companion/model swaps |
| `BonzaiSkillRegistry` / `BonzaiSkillOwnership` | Skill purchase and companion co-owner revenue |

## Provider network

Provider contracts register compute capability and process configured paid inference/service-time rewards. Exact active payment rails depend on the released deployment.

## Storage rule

Contracts store compact proofs: hashes, URIs, ownership, licenses, validation, and revenue routes. Large models, media, datasets, and private memory do not belong onchain.
