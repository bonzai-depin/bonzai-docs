# Architecture

This reference explains how the shipped products fit together without serving as a development guide.

## Product boundary

| Product | Runtime and responsibility |
| --- | --- |
| BonzAI Web | Browser-local introduction and chat on supported devices |
| BonzAI+ | Extension side panel, browser model cache, capture, Live, Imagine, Contribution Packs |
| BonzAI Desktop | Native private studio, local AI services, SQL-backed memory/work records, wallet, P2P, training, companions, teams, and markets |

## Desktop inference

- Local language models use the bundled OpenAI-compatible language-model service.
- Image, audio, music, video, vision, training, and abliteration use the local Python inference service.
- Interactive 3D uses generated Three.js/WebGL scenes.
- P2P can route a supported job to another provider only when the user chooses the network mode.

## Data layer

- SQL repositories store structured local records.
- Embeddings support local semantic memory recall.
- Model/media artifacts live in local file storage.
- Connector secrets use operating-system encryption where available.
- Published metadata/media use configured IPFS/Pinata-compatible storage.
- Onchain registries store compact proofs and economic routes.

## Memory scopes

User, companion identity, team-role, and job memories are distinct scopes. This enables continuity without mixing unrelated businesses or clients.

## Economy chain

v4 economy services derive their network from release configuration rather than assuming Base. Deployment tooling supports configured Ethereum, Arbitrum, or Base deployments and writes address records for the application.
