# Companion Economy

Companions are AI characters with local personality, optional onchain identity, autonomous wallets, tokenization, skills, and revenue paths.

## Scenario

A user creates a companion in Desktop, mints it, lets it use skills, and optionally launches a token.

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

A companion owner can launch an ERC-20 token for the companion. The current factory flow uses:

- 1 billion token supply.
- 96% paired into Uniswap V4 liquidity.
- 4% sent to the companion wallet.
- LP effectively locked/burned at the dead address.

The Uniswap V4 hook routes swap fees across the companion wallet, NFT owner, treasury, and MintPool.

## Universal Profiles

LUKSO Universal Profiles are optional identity extensions. They do not replace companion NFTs and do not mean BonzAI mints companions on LUKSO.
