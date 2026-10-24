# Trading fees and locked liquidity

This page describes the current Desktop guide’s agent, model and game token flows. Historical factories and pools can follow other rules. Inspect the selected token’s actual pool and contracts before applying these percentages.

## What is locked?

The current issuance flows use a permanently locked liquidity principal. Collecting trading fees does not withdraw that principal. Locked liquidity does not eliminate market, contract or price risk, or guarantee a liquid exit.

## Where the 1% trading fee goes

| Beneficiary | Agent pool fee income | Model/game pool fee income |
| --- | ---: | ---: |
| Agent execution wallet | 35% | — |
| Agent NFT owner | 35% | — |
| Creator | — | 70% |
| Treasury | 20% | 20% |
| Staking rewards | 10% | 10% |

These are shares of collected fees, not of liquidity principal. A registered contributor allocation can direct the model creator portion to contributors; metadata alone does not establish a payout.

## Collect and claim

1. Open **Markets**, choose the issued token and open **Trading fees**.
2. Collect pool fees to credit their beneficiaries. Anyone may trigger collection; that does not entitle the caller to every share.
3. Use **Claim my fees** for each currency you are eligible to receive.
4. **Deposit rewards** forwards the reward allocation to the staking basket.

Previously credited balances remain with the original recipient. A later ownership transfer does not rewrite those credits.

Pool deployment and a compatible exchange are prerequisites for trading. A quote can include pool fees, slippage and gas, and the final wallet confirmation governs the transaction.

[Trading-fee walkthrough](guide.md#collect-trading-fees) · [Markets](token-markets.md) · [Rewards](reward-structure.md)
