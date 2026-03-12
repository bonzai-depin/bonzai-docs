# Installation & Setup

## Download

Download the latest release from [bonzai.sh](https://bonzai.sh) or the [GitHub Releases](https://github.com/bonzai-depin/bonzai-desktop-dapp/releases) page.

BonzAI is available as a macOS DMG. Windows and Linux builds are planned.

## First Launch

1. **Open the DMG** and drag BonzAI to your Applications folder
2. **Launch BonzAI** — the app will start the local inference server automatically
3. **Connect your wallet** (optional) — click the wallet icon in the bottom bar

The app is fully functional without a wallet. You only need a wallet to mint NFTs, purchase companions, or participate in the P2P network.

## Development Setup

If you want to build from source:

```bash
# Clone the repository
git clone https://github.com/bonzai-depin/bonzai-desktop-dapp.git
cd bonzai-desktop-dapp

# Install Node.js dependencies
npm install

# Install Python dependencies (for ML inference)
pip install -r src/server/requirements.txt

# Start in development mode (Electron + hot reload + Flask)
npm run start
```

### Environment Variables

Create a `.env` file in the project root:

```env
# Required for NFT metadata uploads
VITE_PINATA_JWT=your_pinata_jwt_token

# Optional
BONZAI_SERVER_PORT=65000        # Flask server port (default: 65000)
OPENCLAW_API_PORT=3002          # OpenClaw LLM port (default: 3002)
```

## Wallet Support

BonzAI supports the following wallets via Reown AppKit:

- MetaMask
- Coinbase Wallet
- Trust Wallet
- Rabby
- WalletConnect (QR code for mobile wallets)

## Supported Networks

| Network | Chain ID | Purpose |
|---------|----------|---------|
| Ethereum | 1 | BONZAI token |
| Arbitrum | 42161 | BONZAI token |
| Base | 8453 | Protocol contracts, companion NFTs, content NFTs |
| LUKSO | 42 | LSP8 content NFTs, Universal Profiles |
