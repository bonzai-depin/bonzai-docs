# Staking

Staking locks `$BONZAI` in the configured BonzAI Staking Vault and creates utility weight.

## Before staking

Check the selected network, vault address, token approval, amount, and lock duration. A locked position cannot be withdrawn before its lock expires.

## Lock choices

| Lock | Weight multiplier |
| --- | ---: |
| Flexible | 1.00× |
| 30 days | 1.10× |
| 90 days | 1.25× |
| 180 days | 1.45× |
| 365 days | 1.70× |

You can extend an active lock. Extending does not require withdrawing first.

## Contribution multiplier

The vault stores a score from 0 to 10,000, set by the owner or an authorized attestor. The multiplier is:

```text
1.00× + contribution score / 10,000
```

The maximum contribution multiplier is therefore 2.00×.

## Revenue Router

The current default split for revenue deposited into a contribution route is:

| Portion | Default |
| --- | ---: |
| Protocol treasury | 10% |
| Immutable base contribution pool | 80% |
| Separate staking bonus | 10% |

The 80% contribution pool follows the route's fixed base shares. The 10% bonus is distributed using active utility weight and contribution score. If no recipient has bonus weight, that unused bonus goes to treasury.

Once a route has received revenue, its recipients and base shares cannot be replaced. This prevents a publisher from removing data owners after an asset starts earning.

## Deployment state

The application and contracts are implemented, tested, and address-configurable. A production transaction is available only after the relevant v4 contracts have been deployed and their addresses added to the released application. The UI should treat a missing address as unavailable, not as a simulated stake.
