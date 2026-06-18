# Provider Rewards

Provider mode lets a user share local compute with the network and become eligible for provider-side pool rewards.

## Scenario

A user with a capable machine runs BonzAI Desktop in Provider mode.

## What Happens

1. The user starts Desktop and selects Provider mode.
2. The provider advertises supported pipelines, peer information, and capabilities.
3. Other users can discover the provider through LAN discovery or the configured provider registry.
4. Requests are served by the provider's local machine.
5. Provider service time is recorded.
6. After an epoch finalizes, the provider can claim a share of provider-side MintPool rewards.

## Provider Reward Formula

Provider rewards are proportional to service time:

```text
provider reward = provider seconds / total provider seconds * provider-side pool amount
```

The MintPool provider side is funded whenever pool deposits are split between holder rewards and provider rewards. The default split is 50% holder side and 50% provider side.

## Requirements

Provider reward claims require:

- Registered provider identity where the registry path is used.
- Recorded service time for the epoch.
- BONZAI balance meeting the configured provider threshold at record/claim time.
- Finalized epoch.

Older direct x402 ETH/USDC payment rails may exist in code, but the current reward documentation should treat service-time pool rewards as the default provider economy.
