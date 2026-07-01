# Payments & Rewards

## Direct paid inference

For an enabled remote x402 flow:

1. The consumer selects a provider and priced pipeline.
2. BonzAI displays the payment requirement.
3. The wallet signs the structured payment authorization.
4. The provider performs the accepted inference.
5. The payment contract settles ETH on the configured network.
6. The platform retains its configured fee (currently 2.5% in the Desktop service configuration).

Never approve a payment whose provider, chain, amount, or pipeline differs from what you selected.

## Service-time rewards

Where Provider Registry, ServiceTime, and MintPool contracts are configured, completed service time can contribute to provider-side epoch rewards:

```text
provider share = provider eligible seconds / total eligible seconds
```

The epoch must finalize before a claim, and block-gap protections apply.

## v4 contribution routes

Provider time can also become a Proof-of-Contribution record for an asset/job route. This is distinct from direct request payment and legacy MintPool epochs.
