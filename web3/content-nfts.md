# Content NFTs

AI-generated content (text, images, audio, video, 3D, training data) can be minted as NFTs on Base and LUKSO.

## Base (ERC-721)

- **Contract**: [`0xdcCF8d2A328F87eDC304898a35F9798ad5Bf87e9`](https://basescan.org/address/0xdcCF8d2A328F87eDC304898a35F9798ad5Bf87e9)
- **Mint fee**: 0.0025 ETH
- **Standard**: ERC-721 with ERC-2981 royalties (7.5%) and ERC721-C transfer validation

### Fee Distribution

| Recipient | Share |
|-----------|-------|
| Treasury | 80% |
| MintPool (content-type pool) | 20% |

### Content Types

| Type | Index | Required Level |
|------|-------|---------------|
| Text | 0 | LVL1 (1,000 BONZAI) |
| Audio | 1 | LVL2 (5,000 BONZAI) |
| Image | 2 | LVL3 (10,000 BONZAI) |
| Video | 3 | LVL4 (25,000 BONZAI) |
| 3D Object | 4 | LVL5 (33,000 BONZAI) |
| Training | 5 | LVL6 (50,000 BONZAI) |

## LUKSO (LSP8)

- **Standard**: LSP8 (NFT 2.0) with Universal Profile support
- **Mint fee**: 15 LYX

## Minting Process

1. **Generate content** using any AI pipeline (free)
2. **Click "Mint"** on the generated content
3. **Content uploaded** to IPFS via Pinata
4. **Metadata JSON** created and uploaded to IPFS
5. **On-chain mint** — calls `BonzaiContent.mint()` with the IPFS metadata URI
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
