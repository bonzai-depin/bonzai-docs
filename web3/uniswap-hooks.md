# Uniswap V4 Hooks

BonzAI uses a custom Uniswap V4 `afterSwap` hook to capture fees from companion token and fine-tune/model token swaps. Hook fees are accumulated and claimed/distributed through contract functions rather than being a normal offchain payment flow.

## Companion Token Hook Split

When a companion token swap generates hook fees:

| Recipient | Share |
| --- | ---: |
| Companion agent wallet | 40% |
| Companion NFT owner | 40% |
| Treasury | 10% |
| MintPool | 10% |

The MintPool share is spread across all six content buckets according to hook logic.

## Fine-Tune / Model Token Hook Split

When a fine-tune or model token swap generates hook fees:

| Recipient | Share |
| --- | ---: |
| Model/fine-tune creator | 80% |
| Treasury | 10% |
| MintPool | 10% |

The MintPool share is spread across all six content buckets.

## Companion Token Launch

The companion token factory creates an ERC-20 token and initializes Uniswap V4 liquidity. The current launch pattern uses:

- 1 billion total supply.
- 96% paired into Uniswap V4 liquidity.
- 4% sent to the companion wallet.
- LP effectively locked/burned at the dead address.

The companion NFT owner must own the companion to launch its token.

## Claiming Hook Fees

Hook fees accrue inside the hook accounting system. Claim functions route accumulated shares to beneficiaries, treasury, and pools.

## Why This Matters

The hook makes companion and model tokens economically useful beyond trading. Swaps can route value to:

- The companion's autonomous wallet.
- The companion owner.
- The model/fine-tune creator.
- Treasury.
- MintPool participants and providers.
