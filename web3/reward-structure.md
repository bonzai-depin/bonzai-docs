# Understand rewards before claiming

BonzAI has several independent sources of potential earnings. Neither staking, owning a token nor running a provider guarantees income. A claim requires the relevant deployed contracts, funded balances and eligibility.

| Source | Where to look | What creates a claim |
| --- | --- | --- |
| Staking basket | Rewards → Your share of the activity | Eligible shares of funded, closed periods, separately for each currency |
| Epoch pools | Rewards → Epoch Pool Rewards | Registered eligible stake and a finalized funded epoch, with its claim steps |
| Token trading fees | Markets → Trading fees | Collected pool fees credited to the beneficiary |
| Remote workflow jobs | The job/escrow flow | Accepted delivery or the applicable dispute/refund outcome, followed by withdrawal |
| Provider pool | Network and provider-related rewards | Independently verified service receipts, finalized periods and enabled claims |
| Contribution allocations | The specific model/job revenue flow | Explicitly registered allocations and actual revenue; attribution alone is not a payout |

## Trading fees in the current issuance flow

The current guide describes a **1% pool trading fee**. Agent fee income is allocated 35% to the execution wallet, 35% to the NFT owner, 20% to treasury and 10% to rewards. Model and game fee income is allocated 70% to the creator, 20% to treasury and 10% to rewards. These describe fee income, not the liquidity principal or a share of every token holder’s balance.

Collecting fees and claiming your credited share are distinct actions. The collector does not receive everyone’s fees. Credited balances remain with their original recipients; liquidity principal stays locked. Historical contracts can differ.

## Staking rewards

Refresh the claimable balance for each closed period and currency. Claim each currency separately; no automatic conversion is implied. Leaving the stake does not erase already accrued claims. Withdrawal notice and any lock still apply to the principal.

## Provider limits

A local service-time ledger is not proof of onchain earnings. The current application guide says independently verified receipts and funded end-to-end settlement must be validated before provider rewards can launch. Do not interpret elapsed processing time as an hourly wage or a withdrawable balance.

[All claim walkthroughs](guide.md#claim-staking-rewards) · [Trading fees](uniswap-hooks.md) · [Staking](staking-architecture.md)
