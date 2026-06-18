# Provider Rewards

BonzAI provider rewards are currently best understood as service-time rewards, not direct per-request checkout payments.

## Current Default: Service-Time Rewards

Provider-side rewards come from the provider share of MintPool deposits.

```text
provider reward = provider seconds / total provider seconds * provider-side pool amount
```

## Provider Claim Flow

1. Run BonzAI Desktop in Provider mode.
2. Register or advertise provider capabilities where the registry path is enabled.
3. Serve inference requests.
4. Record service time for the epoch.
5. Wait for the epoch to finalize.
6. Claim provider rewards from the service-time/MintPool flow.

## Funding Source

Whenever funds enter a MintPool bucket, the deposit is split into:

- Holder side.
- Provider side.

The provider side funds service-time rewards.

## x402 / Direct Payment Rails

BonzAI code may include x402-inspired payment infrastructure for direct ETH/USDC request payments. Treat these as legacy, optional, or future rails unless the product UI explicitly presents them as the active flow.

For current user-facing docs, do not imply that P2P inference always costs ETH/USDC per request.
