# Publish and Mint Assets

Minting is the path from local output to an ownable onchain asset.

Publishing is broader: it can mean making a dataset, model, skill, companion, provider, or company asset visible in the BonzAI economy.

## Scenario

A user generates an image, audio clip, video, text, 3D scene, dataset, or training artifact in BonzAI Desktop and wants to make it ownable or reusable.

## What Happens

1. The user generates or imports the asset locally.
2. Desktop prepares metadata: title, description, media reference, content type, creator, and contribution references.
3. Desktop attaches provenance, training-material policy, marketplace policy, and optional revenue routes.
4. The app checks wallet connection and the configured minting/staking rules.
5. Metadata/media is uploaded through the configured storage path.
6. The user confirms the transaction.
7. The content NFT, registry record, or tokenized model is created.
8. Future revenue can route through the contribution graph.

## Staked BONZAI In Publishing

Where v4 publishing gates are configured, staked `$BONZAI` affects:

- which assets can be published,
- how much trust a published asset receives,
- whether a dataset/model can enter higher-value markets,
- whether a fine-tune/model token can launch,
- utility and the separate staking bonus.

Legacy level/unlock rules still apply to compatible content NFT contracts. v4 staking is the new shared-economy commitment layer.

## Fee And Revenue Routing

Existing content NFT mint fees may route:

- 80% to treasury,
- 20% to the matching legacy MintPool content bucket.

Contribution-aware flows route asset revenue through registered routes:

```text
asset revenue
-> treasury share
-> immutable base contributor shares
-> separate staking bonus weighted by utility
```

## Royalties

Content NFTs use ERC-2981 royalties where configured. The richer BonzAI model is to preserve provenance so royalties, derivative training revenue, or model-token revenue can include the data/model/skill contributors behind the final asset.
