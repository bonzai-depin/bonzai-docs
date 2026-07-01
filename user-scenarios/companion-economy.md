# Companion Economy

Companions are AI characters with local personality, optional onchain identity, autonomous wallets, tokenization, skills, and revenue paths.

## Scenario

A user creates a companion in Desktop, uses it locally, then optionally mints its identity and economy in one transaction.

## Companion Creation

1. The user opens the companion/roleplay experience.
2. They create or select a companion profile.
3. The companion has personality traits, appearance, voice style, scenario context, memory, and optional content level.
4. The user can roleplay locally without minting.

## Companion Minting

When minted, the companion becomes an ERC-721 + ERC-8004 agent identity. The mint can be:

- **Complete**: profile and metadata are ready before mint.
- **Bare**: minted first with placeholder metadata, finalized later.

Companion mints have a per-wallet cap and are free for permanently unlocked users where supported by the contract.

## Agent Wallet

Each minted companion gets an agent wallet. It can be backed by OWS, Privy server wallets, or legacy deterministic fallback for older flows. The agent wallet is used for autonomous identity and economic actions.

## Skill Co-Ownership

Companions can register as co-owners of skills. Skill purchase revenue routes:

- 80% to the skill co-owner distribution system.
- 20% to treasury.

Inside the co-owner distribution, each eligible companion's weight is:

```text
BONZAI balance of companion wallet * spending profile score
```

If no valid co-owner can receive a share, the amount falls back to treasury.

## Companion Token

When the v4 production factory is configured, companion minting atomically launches its ERC-20 token and liquidity. The factory flow uses:

- 1 billion token supply.
- 96% paired into Uniswap V4 liquidity.
- 4% allocated to the companion economy.
- LP effectively locked/burned at the dead address.

The one-percent Uniswap V4 hook contribution routes 40% to the companion wallet, 40% to the NFT owner, 10% to treasury, and 10% to contribution/Mint pools.

## Universal Profiles

LUKSO Universal Profiles are optional identity extensions. They do not replace companion NFTs and do not mean BonzAI mints companions on LUKSO.
