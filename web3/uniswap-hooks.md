# Uniswap V4 Hooks

BonzAI uses a custom Uniswap V4 `afterSwap` hook to capture fees from companion and model token swaps. The hook is deployed via CREATE2 to ensure the contract address has the correct permission bits.

## How It Works

When someone swaps a companion token or fine-tune model token on Uniswap V4:

1. The swap executes normally on the PoolManager
2. The `afterSwap` hook fires and captures **1% of the swap value**
3. The fee is distributed according to the token type

## Fee Distribution

### Companion Tokens

| Recipient | Share |
|-----------|-------|
| Treasury | 33% |
| Companion NFT owner | 33% |
| Companion agent wallet | 34% |

### Fine-Tune Model Tokens

| Recipient | Share |
|-----------|-------|
| Model creator | 80% |
| Treasury | 10% |
| MintPool (LVL6 training pool) | 10% |

## Token Launch Flow

### Companion Tokens (via CompanionTokenFactory)

1. Call `launchToken()` with your companion's token ID
2. Factory creates an ERC-20 token (1 billion supply)
3. 96% of supply goes to Uniswap V4 LP, 4% to the companion owner
4. LP position is locked at the dead address (`0x...dEaD`) — unruggable
5. The hook is automatically registered for the new pool

**Requirement**: Must own the companion NFT (BonzaiCompanions token).

### Fine-Tune Model Tokens (via FineTuneTokenFactory)

Same flow as companion tokens, but:
- Requires owning the fine-tuned model content NFT (BonzaiContent)
- Hook fees go 80% to creator, 10% treasury, 10% to LVL6 MintPool

## Hook Permissions

The hook address is mined via CREATE2 to contain the correct permission bits:

- **Bit 7**: `afterSwap` — captures fees after each swap
- **Bit 4**: `afterSwapReturnDelta` — modifies output amounts
- **Address flags**: `0x0090` (last 14 bits)

## Claiming Fees

- **Companion owners**: Call `claimBeneficiaryFees()` on the hook contract
- **Treasury**: Call `claimTreasuryFees()`
- **MintPool**: Distributed automatically via `distributeMintPoolFees()`
