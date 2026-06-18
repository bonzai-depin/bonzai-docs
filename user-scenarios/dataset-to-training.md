# Capture, Dataset, Training

This is the Proof-of-Contribution path: useful browsing becomes training material.

## Scenario

A user is researching a topic online and wants to build a high-quality dataset for later BonzAI Desktop training.

## Step 1: Capture In BonzAI+

1. The user opens BonzAI+.
2. They choose Dataset mode.
3. They capture a text or image target from the current page.
4. BonzAI+ stores target data, source URL, page context, and local timestamp.
5. If the target is an image, BonzAI+ stores image data as base64 where available.

## Step 2: Smart Analysis

Smart Analysis uses local browser AI capabilities to generate richer metadata:

- Title.
- Caption.
- Tags.
- Source/context notes.
- Image or text description.
- Quality hints.
- Dataset-ready fields.

The output should be descriptive enough for training, retrieval, evaluation, and provenance.

## Step 3: Contribution Passport

Each saved sample can be treated as a contribution record. The user can mark it as:

- Private only.
- Exportable to Desktop.
- Publishable contribution.
- Training-allowed.
- Commercial-allowed.
- Royalty-bearing.

## Step 4: Export Contribution Pack

BonzAI+ exports a pack containing records, metadata, target data, hashes, and optional signatures. This is still local unless the user shares or publishes it.

## Step 5: Import In Desktop

BonzAI Desktop's Contribution Studio imports the pack and can:

- Validate the schema.
- Preview records.
- Detect duplicates.
- Score quality.
- Split train/eval data.
- Attach contributor metadata.
- Add the imported pack to the local contribution ledger.

## Step 6: Train Or Publish

The user can train locally with the dataset. If they mint or publish an asset:

- Metadata/media is uploaded to IPFS/Pinata where needed.
- Hashes, licenses, owners, and revenue routes can be written to registries when configured.
- BonzAI does not use Irys.
