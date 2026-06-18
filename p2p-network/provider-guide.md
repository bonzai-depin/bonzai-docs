# Provider Guide

Provider mode lets you share your local machine with the BonzAI network and become eligible for provider-side rewards.

## Start Provider Mode

1. Open BonzAI Desktop.
2. Go to the P2P or Network settings.
3. Select **Provider** mode.
4. Choose which pipelines your machine can serve.
5. Start advertising locally and/or through the configured provider registry.

## What Providers Advertise

Provider records can include:

- Peer ID.
- Multiaddresses.
- Supported pipelines.
- Relay information.
- Shard/private inference capabilities.
- Optional pricing or legacy payment metadata where enabled.

## Earnings

The current default earning path is provider-side MintPool rewards:

```text
your service seconds / total provider service seconds * provider-side pool amount
```

Claiming requires the epoch to finalize and the configured provider eligibility checks to pass.

## Operational Tips

- Keep the app running while serving.
- Only advertise pipelines your machine can actually handle.
- Monitor model downloads and backend status before accepting heavy workloads.
- Use LAN provider mode for trusted local setups.
- Use remote provider mode when you want broader discovery through the registry.

## Relationship To x402

Direct ETH/USDC payment rails may exist as infrastructure, but current provider docs should not promise per-request payment as the default user path. The product economy is centered on service time and pool rewards.
