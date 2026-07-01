# Datasets, Tune & Uncensor

Training turns curated examples into a reusable model asset. Uncensor creates an abliterated variant of a compatible language model by reducing learned refusal behavior.

## Import a contribution pack

1. Export a Contribution Pack from BonzAI+ or prepare compatible local data.
2. Open **Train → Tune**.
3. Import the pack.
4. Review records, sources, permissions, quality, duplicates, and ownership.
5. Remove unsuitable examples.
6. Split training and evaluation data.

## Fine-tune

Choose the compatible base model and training settings. BonzAI records the training run, input origins, metrics, and resulting artifact so provenance can follow the model.

## Validate before publishing

Training completion does not automatically mean a model is ready for an economy.

Use **Test model** to validate:

- artifact presence and format;
- readable GGUF or adapter weights;
- valid training metrics;
- model kind and provenance;
- abliteration metrics where applicable.

A token cannot be issued until validation passes.

## Create the model identity

After validation, prepare:

- model/token name;
- ticker;
- plain-language description;
- image;
- metadata and provenance;
- initial ETH liquidity.

BonzAI can generate identity suggestions locally, or you can supply your own.

## Issue a model token

Token issuance is a separate, deliberate step after testing. Fine-tuned and abliterated models use the validated issuance flow. The model receives fixed-supply token economics and permanent liquidity through the configured Uniswap factory.

## Uncensor responsibly

Abliteration is not a promise of truth or safety. It changes refusal behavior; it does not make a model more accurate. Use it lawfully, test it carefully, and do not publish a model that fails validation or its license requirements.
