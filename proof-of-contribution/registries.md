# Registries

BonzAI's contribution economy uses registries to make local AI work discoverable and attributable without putting large files onchain.

## Registry Types

| Registry | Purpose |
| --- | --- |
| `BonzaiContributionRegistry` | Generic contribution records and attribution |
| `BonzaiDatasetRegistry` | Dataset/package identity, hashes, licenses, and contributors |
| `BonzaiModelRegistry` | Model/adaptor identity, source datasets, creator, and revenue routes |
| `BonzaiEvaluationRegistry` | Evaluation/appraisal records and quality signals |

## What Goes Onchain

Registries should store compact facts:

- Hashes.
- Owners/contributors.
- License references.
- Royalty/revenue routes.
- Registry pointers.
- State changes.
- Optional signatures.

## What Does Not Go Onchain

Large assets should not be stored onchain:

- Images.
- Video.
- Audio.
- Full datasets.
- Model weights.
- Raw transcripts.

Use IPFS/Pinata or another configured IPFS-compatible store when publishing requires off-device files. Do not document Irys as an active BonzAI dependency.

## Deployment Status

Registry contracts and app services can exist before public deployment. Product docs should distinguish between:

- **Local/import workflow**: usable without registry deployment.
- **Configured publishing workflow**: usable when registry addresses and storage are configured.
- **Roadmap marketplace workflow**: dashboards, discovery, and markets built on top of published records.
