# Content NFTs

AI-generated content (text, images, audio, video, 3D, training data) can be minted as NFTs on Base.

## Base (ERC-721)

- **Contract**: [`0xdcCF8d2A328F87eDC304898a35F9798ad5Bf87e9`](https://basescan.org/address/0xdcCF8d2A328F87eDC304898a35F9798ad5Bf87e9)
- **Standard**: ERC-721 with ERC-2981 royalties (7.5%) and ERC721-C transfer validation
- Each user gets their own collection clone (ERC-1167 minimal proxy) via BonzaiCollectibles

### Per-Type Mint Fees

Each content type has its own mint fee, progressing naturally with the level system:

| Type | Index | Required Level | Mint Fee |
|------|-------|---------------|----------|
| Text | 0 | LVL1 (1,000 BONZAI) | 0.0005 ETH |
| Audio | 1 | LVL2 (5,000 BONZAI) | 0.001 ETH |
| Image | 2 | LVL3 (10,000 BONZAI) | 0.0015 ETH |
| Video | 3 | LVL4 (25,000 BONZAI) | 0.0025 ETH |
| 3D Object | 4 | LVL5 (33,000 BONZAI) | 0.0035 ETH |
| Training | 5 | LVL6 (50,000 BONZAI) | 0.005 ETH |

> **Free minting for unlocked users**: Users who paid 1 ETH via [BonzaiUnlock](smart-contracts.md) mint all content types for free (0 ETH).

### Fee Distribution

| Recipient | Share |
|-----------|-------|
| Treasury | 80% |
| MintPool (content-type pool) | 20% |

## Minting Process

1. **Generate content** using any AI pipeline (free)
2. **Click "Mint"** on the generated content
3. **Content uploaded** to IPFS via Pinata
4. **Metadata JSON** created and uploaded to IPFS
5. **On-chain mint** — calls `BonzaiCollectibles.mint()` with the IPFS metadata URI
6. **Token ID** returned from the `ContentMinted` event

### Metadata Format

Content NFTs use standard ERC-721 metadata with provenance fields:

```json
{
  "name": "AI-Generated Image #42",
  "description": "Created with BonzAI using FLUX",
  "image": "ipfs://...",
  "external_url": "https://bonzai.sh",
  "attributes": [
    { "trait_type": "Content Type", "value": "image" },
    { "trait_type": "Model", "value": "flux-klein" },
    { "trait_type": "Generator", "value": "BonzAI" }
  ]
}
```

## Secondary Royalties

The BonzaiRoyaltySplitter contract distributes secondary sale royalties:

| Recipient | Share |
|-----------|-------|
| Treasury | 2/3 |
| MintPool (weighted by activity) | 1/3 |
