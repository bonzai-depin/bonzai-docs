# Dataset Mode

Dataset mode turns a captured text or image into a rich, traceable training record.

## Choose the target type

- **Text:** the target data is selected text.
- **Image:** the target data is the captured image.

In both cases, Smart Analysis uses visual/text understanding and chat completion to create metadata. The type selector changes the dataset target; it does not switch to Chat mode.

## Smart Analysis

1. Capture a target on the page.
2. Open Dataset.
3. Confirm the target preview. Image mode displays the current image at the top.
4. Choose Text or Image.
5. Select **Smart Analysis**.

BonzAI+ proposes:

- a useful title;
- a rich factual caption;
- deduplicated tags;
- source and page context;
- quality and curation metadata.

The analysis should fail visibly and preserve your target if the model cannot complete the task.

## Review before saving

Small local models can be wrong. Check names, visible text, factual claims, duplicate tags, licensing, and whether the caption describes the target instead of repeating page metadata.

## Contribution Passport

Choose how the record may be used:

- private only;
- exportable to Desktop;
- publishable contribution;
- training allowed;
- commercial use allowed;
- royalty-bearing.

You can optionally add a wallet address for Web3 attribution. A wallet is not required to save private data.

## Image records

Where browser access permits, image data is saved as base64 alongside its URL, caption, tags, and provenance. This makes the pack more portable when the original page later changes.

## Export

Use **Contribution Pack** to export records for BonzAI Desktop. The pack includes schema version, content hashes, sources, permissions, quality signals, and contribution metadata.
