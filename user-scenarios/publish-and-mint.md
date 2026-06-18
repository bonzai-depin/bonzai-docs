# Publish and Mint Assets

Minting is the path from local output to an ownable onchain asset.

## Scenario

A user generates an image, audio clip, video, text, 3D scene, or training artifact in BonzAI Desktop and wants to mint it.

## What Happens

1. The user generates or imports the asset locally.
2. Desktop prepares metadata: title, description, media reference, content type, creator, and optional contribution references.
3. The app checks wallet connection and BONZAI level or permanent unlock.
4. Metadata/media is uploaded to IPFS through Pinata or a configured IPFS path.
5. The user confirms the mint transaction.
6. The content NFT is minted.
7. Mint fees are routed through the configured fee split.

## Content-Type Levels

| Type | Level | BONZAI threshold |
| --- | --- | --- |
| Text | LVL1 | 1,000 |
| Audio | LVL2 | 5,000 |
| Image | LVL3 | 10,000 |
| Video | LVL4 | 25,000 |
| 3D | LVL5 | 33,000 |
| Training | LVL6 | 50,000 |

The one-time unlock grants all levels and makes content and companion mints free where supported by the contracts.

## Fee Routing

Content NFT mint fees route:

- 80% to treasury.
- 20% to the matching MintPool content bucket.

The MintPool deposit is split between holder rewards and provider rewards according to the contract configuration, defaulting to 50/50.

## Royalties

Content NFTs use ERC-2981 royalties where configured. The royalty splitter routes secondary royalties according to the protocol setup, including treasury and pool allocations.
