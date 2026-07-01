# Content NFTs

BonzAI content NFTs let users mint locally generated assets as onchain collectibles. Normal generation is free; minting is the economic action.

## Supported Content Types

| Type | Level | Example |
| --- | --- | --- |
| Text | LVL1 | Stories, prompts, essays, chat outputs |
| Audio | LVL2 | Voice, music, sound outputs |
| Image | LVL3 | Generated images |
| Video | LVL4 | Generated clips |
| 3D | LVL5 | Generated Three.js scenes/assets |
| Training | LVL6 | Training artifacts, fine-tune assets, dataset-derived outputs |

## Mint Flow

1. Generate or import the asset in Desktop.
2. Connect a wallet.
3. Desktop checks level or permanent unlock.
4. Metadata/media is uploaded to IPFS/Pinata or configured IPFS-compatible storage.
5. The user confirms the mint transaction.
6. Mint fees route through treasury and MintPool.

The owner can optionally make an eligible minted generation discoverable in the marketplace. NSFW generations are excluded from marketplace discovery.

Private files stay local until the user chooses to mint. Published metadata and media use the storage path configured in the app, such as IPFS pinning.

## Per-Type Mint Fees

| Type | Fee |
| --- | ---: |
| Text | 0.0005 ETH |
| Audio | 0.001 ETH |
| Image | 0.0015 ETH |
| Video | 0.0025 ETH |
| 3D | 0.0035 ETH |
| Training | 0.005 ETH |

Unlocked users can mint for free where supported.

## Fee Split

```text
content mint fee
-> 80% treasury
-> 20% matching MintPool content bucket
```

The MintPool deposit is then split into holder-side and provider-side reward accounting.

## Royalties

Content NFTs support ERC-2981 royalties where configured. The royalty splitter can route secondary royalties between treasury and pool rewards.

## LUKSO

BonzAI supports LUKSO Universal Profiles for companion identity. Do not assume content NFT minting is active on LUKSO unless a LUKSO content contract is explicitly configured in the app environment.
