# Registries

Registries are how BonzAI can publish proof without putting large files onchain.

They store compact records: hashes, owners, licenses, attribution, and reward routes.

## Why Registries Exist

A model, dataset, skill, or generated asset can have many contributors. A registry gives the ecosystem a shared place to say:

- This asset exists.
- This hash identifies it.
- This wallet published it.
- These contributors helped make it useful.
- This license applies.
- This is how revenue should be routed.

## Registry Types

| Registry | Tracks |
| --- | --- |
| Contribution Registry | Individual useful contributions |
| Dataset Registry | Dataset packs, licenses, contributors, and hashes |
| Model Registry | Models, adapters, training sources, and creator routes |
| Evaluation Registry | Ratings, tests, appraisals, and quality signals |

## What Stays Offchain

Large files stay outside the contract:

- Images.
- Video.
- Audio.
- Full datasets.
- Model weights.
- Raw transcripts.

The chain only needs the proof and routing data.

## Current Status

The local workflow works before registries are deployed:

1. BonzAI+ captures records.
2. Desktop imports them.
3. Desktop tracks them in a local ledger.
4. Publishing becomes available when registry addresses and storage are configured.
