# Companions

BonzAI companions are autonomous AI agents with on-chain identity. Each companion is an ERC-721 NFT on Base that implements the [ERC-8004](https://eips.ethereum.org/EIPS/eip-8004) Identity Registry standard.

## What Makes a Companion

Each companion has:

- **Personality** — Big 5 (OCEAN) personality traits that influence behavior and dialogue
- **Spending Profile** — 12-category preference system stored on-chain as a packed `uint96`
- **Agent Wallet** — An autonomous wallet for receiving payments and executing transactions
- **Voice** — Unique TTS voice persona for spoken responses
- **Visual Identity** — Generated portrait stored on IPFS

## 13 Default Companions

BonzAI ships with 13 pre-built companions available for roleplay without minting:

| Name | Gender | Age | Type |
|------|--------|-----|------|
| Aurore Beaumont | Female | 28 | Human |
| Mai Tanaka | Female | 32 | Human |
| Marcus Ferrara | Male | 35 | Human |
| James Whitmore | Male | 40 | Human |
| ARIA-7 | Female | N/A (appears 25) | Android |
| KAI-9 | Male | N/A (appears 30) | Android |
| Damon Rivers | Male | 34 | Human |
| Zara Okonkwo | Female | 29 | Human |
| Jin Chen | Male | 31 | Human |
| Priya Sharma | Female | 30 | Human |
| Arjun Kapoor | Male | 36 | Human |
| Sofia Reyes | Female | 27 | Human |
| Miguel Santos | Male | 33 | Human |

Default companions are free to use but cannot be minted as NFTs. To create a companion NFT with an on-chain identity, see the [Minting Guide](minting-guide.md).

## Roleplay System

The companion roleplay system features:

- **13 scenario locations** (art gallery, private kitchen, jungle retreat, etc.)
- **Multi-modal responses** — text, voice, images, and video
- **Memory persistence** across sessions
- **Content levels** — PG, PG-13, Mature, Adult
- **Autonomous mode** — companions act independently when you're away
- **Import/export** companion identity

## On-Chain Features

Minted companions unlock:

- **Skill co-ownership** — Register companions to earn revenue from skill purchases
- **Token launch** — Create an ERC-20 token for your companion with Uniswap V4 LP
- **x402 payments** — Companions can pay for services using their agent wallet
- **Social presence** — Post to Moltbook and respond via OpenClaw/Hermes
