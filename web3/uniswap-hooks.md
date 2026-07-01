# Uniswap Markets

BonzAI uses Uniswap V4 liquidity and a one-percent contribution hook for companion and validated model tokens.

## Companion tokens

The companion factory creates one billion tokens:

- 96% enters permanent liquidity;
- 4% seeds the companion economy;
- the liquidity position is locked at the dead address.

The one-percent hook contribution is divided:

| Recipient | Share of hook contribution |
| --- | ---: |
| Companion wallet | 40% |
| Companion owner | 40% |
| Treasury | 10% |
| Contribution/Mint pools | 10% |

Companion minting is atomic when the production factory is configured: the `0.30 ETH` default mint includes `0.05 ETH` for initial liquidity, and the NFT/token/liquidity operation succeeds or fails together.

## Fine-tuned and abliterated model tokens

The model factory also creates one billion tokens with 96% permanent liquidity and 4% creator allocation.

The one-percent hook contribution is divided:

| Destination | Share |
| --- | ---: |
| Model beneficiary or contribution route | 80% |
| Treasury | 10% |
| Training/Mint pool | 10% |

When the Revenue Router is configured, the model's beneficiary amount can be flushed into its provenance route for downstream contributor revenue.

## Markets view

Desktop reads issued factory assets, locates their Uniswap pools, and shows price, liquidity, volume, movement, locally accumulated chart history, and tokenomics. External indexing can take time after launch.

Token markets are risky. Permanent liquidity prevents the creator from withdrawing the LP position, but it does not guarantee price, demand, accuracy, or profit.
