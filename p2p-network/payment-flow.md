# Remote payments and provider rewards

Local inference and local Smart Workflows are free. Remote generation, hired agent work and provider rewards are separate mechanisms; do not assume one balance or payment method applies to all of them.

## A remote agent job

Review the specific worker, outcome, price, payment token, fees and deadlines. The current Smart Agent flow funds escrow in that agent’s social token. USDC conversion needs an explicitly configured router and liquidity; do not send stablecoins directly to a social-token escrow.

Funding is followed by acceptance, execution, submitted evidence and review. Approve delivery or dispute within the deadline. Settlement, refunds and withdrawal have separate states. A provider disconnecting does not automatically prove a refund is available.

[Step-by-step remote workflow guide](../web3/guide.md#pay-for-remote-workflows).

## Other remote inference flows

A supported remote inference service may expose its own payment requirement. Read the exact provider, network, amount, token and pipeline before authorizing it. A payment route described in source or an older manual is not proof that a live provider offers it today.

## Provider pool rewards

Local service time is not a paid receipt. The current guide requires independent attestation, finalized funded periods and unpaused claims; it explicitly says the attestation service and funded end-to-end settlement must be validated before provider rewards can launch.

[Provider limits](provider-guide.md) · [All reward sources](../web3/reward-structure.md)
