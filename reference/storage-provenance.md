# Storage & Provenance

## Local storage

BonzAI Desktop uses a structured local SQL database for durable application records, including memory notes and job data. Large model files and generated media use local filesystem storage suited to their size.

BonzAI+ uses extension/browser storage for settings, histories, datasets, and cached browser model assets.

## Publishing storage

When the user publishes or mints, BonzAI uses its configured IPFS/Pinata-compatible storage path for metadata and media. Contracts record content identifiers, hashes, ownership, validation, licenses, and routes.

## No Irys

BonzAI does **not** use Irys. Documentation, onboarding, and transaction explanations must not describe an Irys upload or balance requirement.

## Provenance

Provenance records known parents of an asset: captured sources, dataset records, training run, model, prompt/caption work, evaluators, owners, and derived outputs. It makes attribution inspectable; it cannot prove facts that were never recorded.
