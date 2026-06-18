# Contribution Packs

A Contribution Pack is the local-first package format that moves useful work from BonzAI+ into BonzAI Desktop.

## Purpose

Contribution Packs make datasets and AI work portable without losing provenance. A pack can remain private, be imported into Desktop, or later become a publishable contribution.

## Record Fields

A contribution record should include:

| Field | Meaning |
| --- | --- |
| `type` | Contribution type, such as `dataset_text`, `dataset_image`, `dataset_video`, `generation`, or `evaluation` |
| `content_hash` | Hash of the target content or normalized payload |
| `source_url` | Where the sample came from, when available |
| `local_timestamp` | Capture/import time on the user's device |
| `creator_wallet` | Optional wallet attribution |
| `license` | User-selected license or usage permission |
| `quality_score` | Local quality/appraisal score |
| `tags` | Human/model-generated tags |
| `model_task_target` | Intended task, model, or training target |
| `privacy_status` | Private, exportable, publishable, or commercial/training allowed |
| `provenance` | Capture method, page context, model used, transformation path |
| `evidence_files` | Base64 image data, thumbnails, transcripts, or companion files |
| `signature` | Optional local/wallet signature for integrity |

## Permission Flags

BonzAI+ should let a user mark samples as:

- Private only.
- Exportable to Desktop.
- Publishable contribution.
- Training-allowed.
- Commercial-allowed.
- Royalty-bearing.

## Storage

Contribution Packs are local files until the user publishes or mints. If off-device storage is needed, use IPFS/Pinata or explicitly configured IPFS-compatible storage. BonzAI does not use Irys.
