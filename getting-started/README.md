# Getting Started

BonzAI can be used without a wallet. A wallet is only needed when you want to mint, publish, register/claim rewards, launch tokens, or use other onchain economy features.

## Choose A Product

| Product | Start here if you want to... |
| --- | --- |
| BonzAI Web | Try local browser AI and learn the product suite |
| BonzAI+ | Capture web text/images, follow video, generate images in-browser, or build datasets |
| BonzAI Desktop | Run the full local studio, train, mint, manage companions, or provide compute |

## Desktop Setup

1. Download BonzAI Desktop from the official BonzAI site or release channel.
2. Install the app.
3. Launch it and let the local backends initialize.
4. Download the models you want to use.
5. Generate locally without connecting a wallet, or connect a wallet for onchain features.

## Development Setup

```bash
npm install
pip install -r src/server/requirements.txt
npm run start
```

Desktop runs:

- Electron/Vue UI.
- OpenClaw for LLM chat completions.
- Flask backend for image, audio, video, music, and vision.
- Optional P2P node.

## Wallets

Connect a wallet when you want to:

- Check BONZAI balance/level.
- Mint content NFTs.
- Mint companions.
- Launch companion/model tokens.
- Register as a provider.
- Claim MintPool or provider rewards.
- Publish records to configured contribution registries.

## Networks

BonzAI is multi-chain, but exact contract addresses are configuration-driven. The product currently uses:

| Network | Role |
| --- | --- |
| Ethereum | BONZAI token and configurable app-chain deployments |
| Arbitrum | BONZAI token |
| Base | BONZAI token, Uniswap V4, and historical/Base deployment paths |
| LUKSO | Optional Universal Profiles for companions |

LUKSO Universal Profiles are identity extensions. Do not assume every NFT or payment flow runs on LUKSO.

## Storage

BonzAI does not use Irys. Published metadata and media use IPFS/Pinata or an explicitly configured IPFS-compatible path.
