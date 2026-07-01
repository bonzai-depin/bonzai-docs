# Desktop Contribution Studio

The Contribution Studio turns browser captures and local records into reviewed training material.

## Import and inspect

1. Import a BonzAI+ Contribution Pack.
2. Validate its schema and hashes.
3. Preview records and media.
4. inspect sources, permissions, wallet attribution, and quality.
5. remove duplicates, private data, unsupported formats, and weak examples.
6. split records into training and evaluation groups.

## Train with provenance

The training run records known source records, data-owner wallets, dataset identity, metrics, resulting files, and model kind. LLM adapters/GGUF artifacts and diffusion training have different technical limits, but both preserve a provenance manifest alongside the resulting model whenever possible.

## Validate

Use **Test model** after training. Validation checks artifact format/presence, metrics, and model kind and creates a validation hash. Fine-tuned and abliterated model token issuance remains disabled until validation passes.

## Publish deliberately

Private training needs no wallet. Registry publication, minting, model token issuance, and contribution revenue routes require the configured contracts, storage path, wallet confirmation, and any applicable staking/minting eligibility.
