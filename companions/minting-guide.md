# Create & Mint a Companion

Companions work locally without minting. Mint only when you want portable onchain identity, an agent wallet, jobs/skills economics, or a companion token market.

## Create locally

1. Open the companion experience.
2. Choose or create an identity.
3. Set personality, background, appearance, voice, and boundaries.
4. Generate or upload a portrait.
5. Start a conversation and confirm the companion feels right.

## Before minting

- Connect the intended owner wallet.
- Select the configured economy network.
- Check the displayed mint amount and gas.
- Review public metadata.
- Confirm the wallet has not reached its companion cap.

## Atomic v4 mint

The default contract price is **0.30 ETH**. When the companion token factory is configured, **0.05 ETH** seeds token liquidity and the mint atomically creates:

- the companion NFT/agent identity;
- its one-billion-supply token;
- permanent Uniswap liquidity;
- companion owner/wallet economic links.

If token or liquidity creation fails, the entire transaction reverts.

## After minting

The companion can keep local memory, use its agent wallet, participate in skills and jobs, build verified reputation, and appear in Earn → Markets. The onchain identity does not publish private conversations or team memories.
