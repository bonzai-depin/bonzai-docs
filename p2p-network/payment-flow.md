# Payment Flow (x402)

BonzAI uses an HTTP 402-inspired payment protocol for P2P inference. Payments are processed on **Base** (chain ID 8453) in ETH or USDC.

## Protocol Overview

The x402 flow follows a challenge-response pattern:

1. **Consumer** sends inference request to provider via libp2p
2. **Provider** returns `402 Payment Required` with amount and address
3. **Consumer** sends payment (ETH or signed EIP-712 authorization)
4. **Consumer** retries request with payment proof (tx hash)
5. **Provider** verifies payment on-chain, processes inference, returns result

## Payment Methods

### Direct ETH Payment

The simplest flow — consumer sends ETH directly:

```
Consumer → BonzaiPayment.payDirectETH(provider, service) + msg.value
```

### Direct USDC Payment

Consumer approves and sends USDC:

```
Consumer → USDC.approve(BonzaiPayment, amount)
Consumer → BonzaiPayment.payDirect(provider, amount, service)
```

### Pre-Deposited Balance

For faster payments, consumers can pre-deposit funds:

```
// Deposit
Consumer → BonzaiPayment.depositETH() + msg.value
Consumer → BonzaiPayment.deposit(usdcAmount)  // after USDC approval

// Pay from balance (no approval needed per-transaction)
Consumer → BonzaiPayment.payFromETHBalance(provider, amount, service)
Consumer → BonzaiPayment.payFromBalance(provider, amount, service)
```

### EIP-712 Signed Authorization

For contract-mediated payments with replay protection:

1. Consumer signs an EIP-712 typed message:
   ```
   Payment(address provider, uint256 amount, uint256 nonce, uint256 expiry, string service, uint8 paymentToken)
   ```
2. Provider submits the signature to `BonzaiPayment.processPayment()`
3. Contract verifies signature, deducts from consumer's deposited balance, distributes funds

**Domain**: `BonzAI x402` version `2`, chain ID `8453`

## Fee Split

On every payment:

| Recipient | Share |
|-----------|-------|
| Provider | 97.5% |
| Treasury | 2.5% |

## Pricing

Providers set a `pricePerToken` (price per 1,000 tokens in wei) during registration.

The consumer's cost is calculated as:

```
estimatedTokens = (inputTokens * 3)  // input + 2x estimated output
totalAmount = ceil(estimatedTokens / 1000) * pricePerToken
```

Minimum: 100 tokens per request.

## Self-Inference

If the consumer and provider are the same node (matching peerId), **no payment is required**. Self-inference is always free.

## Replay Protection

- **On-chain**: Each `(consumer, nonce)` pair can only be used once
- **Off-chain**: Provider maintains a nonce cache in Electron Store (24h TTL, 10K entry cap)
- **Expiry**: Signed payments expire after 5 minutes

## Supported Tokens

| Token | Enum Value | Decimals |
|-------|-----------|----------|
| ETH | 0 | 18 |
| USDC | 1 | 6 |

USDC on Base: [`0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913`](https://basescan.org/token/0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913)
