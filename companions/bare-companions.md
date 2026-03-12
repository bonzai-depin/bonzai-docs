# Bare Companions

Bare companions are a pre-reveal minting flow that lets you mint a companion NFT without completing the full setup immediately. You can finalize the companion's identity later.

## How It Works

### Minting a Bare Companion

1. Call `mintCompanion()` with placeholder metadata (`status: 'pending_setup'`)
2. The NFT is minted with a minimal registration — no portrait, no personality details
3. The companion appears in your collection with a "Needs Setup" badge

### Detection

The app detects bare companions by checking:
- `metadata.bonzai.status === 'pending_setup'`
- `metadata.active === false` and name contains "Pending Setup"

### Finalization

When you're ready, the `finalizeCompanion()` flow completes the setup:

1. **Generate spending profile** from personality description
2. **Generate portrait** using the image pipeline (or provide your own)
3. **Upload image** to IPFS via Pinata
4. **Build full ERC-8004 registration** with OASF v0.8.0 traits
5. **Upload registration JSON** to IPFS
6. **Set agent URI** on-chain via `setAgentURI()`
7. **Create agent wallet** (local deterministic or Privy server wallet)
8. **Set agent wallet** on-chain via `setAgentWallet()`
9. **Set spending profile** on-chain (packed `uint96`)
10. **Set personality hash** on-chain
11. **Set OASF traits** via `setMetadataBatch()`

## Use Cases

- **External minting**: Mint via BaseScan or another dApp, then finalize in BonzAI
- **Batch minting**: Mint several companions quickly, set up their identities later
- **Deferred decisions**: Secure your token ID now, decide on personality and appearance later
