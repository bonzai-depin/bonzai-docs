# Private Local Creation

This is the simplest BonzAI path: a user wants to generate privately without minting, publishing, or joining the economy.

## Scenario

A user opens BonzAI Desktop, BonzAI Web, or BonzAI+ and asks for text, image, audio, video, or analysis.

## What Happens

1. The user enters a prompt or captures a target.
2. BonzAI routes the request to the local browser engine, OpenClaw, or the local Flask backend depending on product and generation type.
3. The model runs locally when supported by the selected product/device.
4. The result is stored in local app history or extension state.
5. No wallet is required.
6. No onchain transaction is created.
7. No IPFS upload happens unless the user later exports, publishes, or mints.

## When A Wallet Becomes Useful

A wallet is only needed for economic actions such as:

- Minting generated assets.
- Minting companions.
- Launching companion or model tokens.
- Registering as a provider.
- Claiming MintPool or provider rewards.
- Publishing records to contribution/model/dataset registries.

## Why This Matters

BonzAI's token economy is layered on top of creation. Normal generation remains available without turning every prompt into a transaction.
