# Contribution Packs

A Contribution Pack is a file that carries useful AI work from BonzAI+ into BonzAI Desktop.

Think of it as a dataset export with receipts: what was captured, where it came from, how it was described, what permissions the user chose, and how it can be reused.

## Why Packs Exist

Without a pack, a dataset is just loose text and images. With a pack, Desktop can understand:

- The original source.
- The captured text or image.
- The generated caption and tags.
- The user rating.
- The license or permission choice.
- Whether the sample is private, exportable, trainable, commercial, or publishable.
- Who should be credited if it becomes part of a larger asset.

## What A Record Can Include

| Field | Meaning |
| --- | --- |
| Type | Text, image, video note, generation, evaluation, skill, model adapter, provider time, or companion/company action |
| Content hash | A fingerprint of the saved material |
| Source URL | Where the material came from |
| Timestamp | When it was captured |
| Creator wallet | Optional attribution |
| License | What the user allows |
| Quality score | How useful the sample seems |
| Tags | Search and training labels |
| Task target | What this record is useful for |
| Privacy status | Private, exportable, publishable, trainable, commercial, or royalty-bearing |
| Evidence files | Image data, thumbnails, transcripts, or other attached proof |
| Signature | Optional proof that the creator approved the record |
| Contribution role | Data owner, curator, evaluator, voter, trainer, provider, publisher, companion, or company |
| Contribution weight | Local or onchain score used to estimate how much this record helped |
| Derivation parents | Earlier records, datasets, models, skills, or companions this record depends on |
| Royalty route | Optional payout route if the record becomes part of a monetized asset |
| BONZAI utility snapshot | Optional local record of stake, lock, contribution score, tier, and utility weight at packaging time; live contracts remain authoritative |

## Local Until The User Acts

Contribution Packs stay local until the user exports, shares, publishes, or mints something from them.

## Why Parent Records Matter

The important part is inheritance. If an image dataset trains an adapter, and that adapter helps a company create a sellable output, the final output should still know which records, curators, evaluators, and model builders helped.

That does not mean everything must go onchain immediately. It means Desktop should preserve the local graph first, then publish compact hashes, licenses, ownership, and reward routes only when the user chooses to enter the shared economy.
