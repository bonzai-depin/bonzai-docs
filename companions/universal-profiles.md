# Universal Profiles (LUKSO)

After minting a companion on Base, you can deploy a **Universal Profile** on LUKSO to give your companion a rich on-chain identity across multiple chains.

## What Is a Universal Profile?

A [Universal Profile](https://docs.lukso.tech/standards/accounts/lsp0-erc725account) (LSP0) is a smart contract account on LUKSO that acts as an on-chain identity. Unlike regular wallets (EOAs), Universal Profiles support:

- **Rich metadata** (LSP3 Profile — name, description, avatar, links)
- **Permission management** (LSP6 Key Manager — granular access control)
- **Universal Receiver** (LSP1 — react to incoming transactions automatically)
- **Multi-chain presence** — same address on multiple chains via deterministic deployment

## How It Works

Companion UP deployment uses the **LSP23 Linked Contracts Factory** at [`0x2300000A84D25dF63081feAa37ba6b62C4c89a30`](https://explorer.lukso.network/address/0x2300000A84D25dF63081feAa37ba6b62C4c89a30) to create two linked contracts:

1. **Universal Profile (LSP0)** — the companion's on-chain account
2. **Key Manager (LSP6)** — permission controller for the UP

The companion's **agent wallet** (OWS, Privy, or legacy deterministic) is set as the LSP6 controller, giving it full permissions to operate the UP. No wallet migration is required — any wallet type can serve as the LSP6 controller.

## Deploying a UP

### From Roleplay Chat

1. Mint your companion on Base first
2. Click the **Universal Profile** button on your minted companion
3. Confirm the network switch to LUKSO
4. Approve the deployment transaction (gas only, no mint fee)
5. Your companion's UP is deployed and linked

### From Browse Agents

1. Select a minted companion
2. Click **Attach Universal Profile**
3. Follow the same confirmation flow

### What Gets Set Up

| Component | Details |
|-----------|---------|
| **LSP3 Profile** | Companion name, bio, and avatar from ERC-8004 metadata |
| **LSP6 Permissions** | Agent wallet gets full controller access |
| **LSP1 Delegate** | Universal Receiver Delegate for handling incoming assets |
| **Deterministic Address** | Salt derived from companion ID for predictable addresses |

## Cross-Chain Replay

Once deployed on LUKSO, the same Universal Profile can be replayed to other chains:

1. The deployment calldata is stored locally in Electron Store
2. Call `deployCompanionUPCrossChain(companionId, targetChainId)` to replay
3. The LSP23 factory at the same address on the target chain deploys the UP
4. **Same UP address** on every chain (deterministic via salt)

Supported replay targets: Base (8453), Ethereum (1).

> **Note**: LSP6 permissions are per-chain. The agent wallet needs to be authorized as a controller on each chain separately.

## Architecture

```
Base (8453)                    LUKSO (42)                  Other Chains
┌─────────────────┐           ┌─────────────────┐        ┌──────────────┐
│ BonzaiCompanions│           │ Universal Profile│        │ Same UP addr │
│ ERC-721 + 8004  │──deploy──►│ (LSP0)          │──replay─►│ (LSP0)      │
│ Token #42       │    UP     │ + Key Manager   │         │ + Key Mgr    │
│ Agent Wallet: 0x│           │   (LSP6)        │         │   (LSP6)     │
└─────────────────┘           └─────────────────┘        └──────────────┘
        │                              │
        └── agent wallet ──────────────┘
            (LSP6 controller on all chains)
```

## Scope

LUKSO integration in BonzAI is strictly for **Universal Profiles**. There is no companion NFT minting, no content/collectible minting, and no x402 payments on LUKSO. All NFT minting and payments happen on Base.

## Current Limitations

- **UP deployment is optional** — companions work fully without a Universal Profile
- **Gas required on LUKSO** — you need LYX to pay for the deployment transaction
