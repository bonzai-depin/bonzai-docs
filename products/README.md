# Product Suite

BonzAI is one system with three user-facing products. Each product has a different job, but they are designed to form a single local AI lifecycle.

## Product Roles

| Product | Primary role | Typical user intent |
| --- | --- | --- |
| **BonzAI Web** | Public local AI surface | Try BonzAI, chat locally, learn the product suite, download/share Desktop binaries |
| **BonzAI+** | Browser capture and assistant layer | Ask about a page, capture text/images, follow video, generate images, curate datasets |
| **BonzAI Desktop** | Full local production studio | Run larger local models, train/fine-tune, mint, manage companions, serve or consume P2P inference |

## How They Work Together

1. A user discovers BonzAI through **BonzAI Web**.
2. They install **BonzAI+** to capture useful web context.
3. BonzAI+ turns browsing into structured samples, images, transcripts, generated images, tags, ratings, and contribution metadata.
4. The user exports those records into **BonzAI Desktop**.
5. Desktop validates/imports the records, trains or generates with them, and can mint or publish resulting assets.
6. Onchain systems route rights, revenue, and reputation back to creators, providers, companion owners, skill co-owners, model creators, and future contribution registries.

## Local-First Does Not Mean One Device Does Everything

BonzAI is local-first, but different surfaces have different constraints:

- Browser AI depends on browser APIs, WebGPU/WebNN availability, memory, and mobile WebKit limitations.
- BonzAI+ runs inside browser extension constraints.
- Desktop can use larger local models, Python backends, GPU/VRAM detection, and Electron-native storage.
- P2P provider mode lets users serve local compute to others while keeping the protocol decentralized.

## No Irys

BonzAI does not use Irys. Published metadata and content should be documented as IPFS/Pinata or another explicitly configured IPFS-compatible path.
