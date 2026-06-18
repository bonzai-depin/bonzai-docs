# Agent Wallets

Every minted companion receives an autonomous wallet — an Ethereum address controlled by the companion, stored on-chain via the ERC-8004 `setAgentWallet()` function.

## Wallet Modes

BonzAI supports three wallet creation modes, selected automatically based on how the user authenticated:

### Open Wallet Standard (Primary)

For users who connect via MetaMask, Coinbase, or other Reown wallets:

- Wallet created in a local OWS vault (encrypted with scrypt/AES-256-GCM)
- Native Rust bindings via NAPI-RS — runs entirely in-process, no server
- Policy-based spending controls (chain allowlists, daily limits, expiry)
- Scoped API keys for autonomous agent operations
- EIP-712 signing support
- Fully self-custodied — vault stored locally in the app data directory

### Privy Server Wallets

For users who authenticate via Privy (email/social login):

- Wallet created via Privy's server wallet API
- Managed by Privy's infrastructure with optional spending policies
- No private key management required from the user

### Local Deterministic (Legacy)

- Wallet derived deterministically: `keccak256(masterSecret + companionId)`
- Private key stored locally in Electron Store
- Still supported for existing companions — new companions use OWS
- Can be migrated to OWS via the "Migrate to OWS" button in Browse Agents

## What Agent Wallets Can Do

- **Receive ETH/tokens** — fund the wallet to enable autonomous transactions
- **Autonomous payments** — companions can pay for enabled onchain actions, including optional/legacy direct-payment rails where the product exposes them
- **Skill purchases** — companions can autonomously purchase skills
- **Social actions** — fund Moltbook posts and interactions
- **Token holdings** — BONZAI balance influences skill co-ownership weight

## On-Chain Storage

The agent wallet address is stored in the BonzaiCompanions contract:

```solidity
// Set during minting or finalization
function setAgentWallet(uint256 tokenId, address wallet) external;

// Query
function getAgentWallet(uint256 tokenId) external view returns (address);
```

Only the NFT owner can set or change the agent wallet.

## LUKSO Universal Profiles

On LUKSO, companions can optionally receive a Universal Profile (LSP0) deployed via the LSP23 factory. The companion's agent wallet (OWS, Privy, or legacy) is set as an LSP6 controller on the Universal Profile, enabling:

- Rich on-chain metadata (LSP3 profile)
- Multi-controller permissions
- Cross-chain replay of deployment calldata

See [Universal Profiles](universal-profiles.md) for full details.
