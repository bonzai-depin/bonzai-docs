# BonzAI+ Browser Assistant

BonzAI+ is the browser extension for BonzAI. It is a focused side-panel assistant, not a clone of BonzAI Web. Its job is to help users understand the current page, capture useful material, generate images locally in the browser when supported, and turn browsing into training-ready datasets.

## Main Modes

| Mode | Purpose |
| --- | --- |
| **Chat** | A simplified BonzAI Web-style chat experience inside the extension. Users can chat freely, chat about a captured text/image target, clear messages, and clear the target. |
| **Live** | Screen/video understanding. BonzAI+ samples visible video/screen content, builds transcript cues, labels highlights, and can send cue text into Imagine as an image prompt. |
| **Imagine** | In-browser image generation using the local browser engine when supported. Prompts and generated images stay on the device. |
| **Dataset** | Dataset curation for text and image targets with Smart Analysis, rich metadata, tags, source context, ratings, base64 image data, and exportable records. |

## Capture Workflow

BonzAI+ can overlay web page text and image targets with a **BonzAI+** capture call-to-action. The overlay can be disabled from the extension header. Capturing a target sets it as the current Chat or Dataset target:

- **Text mode** captures text.
- **Image mode** captures images and stores image data as base64 where available.
- Smart Analysis uses vision/OCR and chat completion to produce richer title, caption, tags, and metadata.

## Live Video Understanding

Live mode is designed to tell the story of what is happening on screen, not merely wait for OCR-backed decisive events. The current direction is:

- Detect the domain and subtype of the visible content.
- Use a subtype event vocabulary and visual evidence checklist.
- Sample scene windows and story frames based on the selected speed/quality setting.
- Emit useful, varied transcript cues with labels such as Goal, Catch, KO, Scene change, Key quote, Score, HUD, Action, and Context.
- Avoid generic fallback captions. If the model cannot describe the current screen, the pipeline should keep probing rather than emit useless template text.

Live mode is browser-extension-local and should work anywhere a user can share a tab/window/screen, not just on YouTube.

## Imagine Mode

Imagine mode adds local image generation to BonzAI+. The UI exposes:

- Resolution selectors: 128, 256, 512, and 1024.
- Speed/quality selectors.
- Generation progress.
- Generated image history.
- Clear and download actions.

The extension caches downloaded models so the user does not redownload them every launch.

## Dataset Mode

Dataset mode prepares training material for BonzAI Desktop. A saved record can include:

- Type: text or image.
- Target data.
- Base64 image payload when the target is an image.
- Source URL and page context.
- Generated title, caption, tags, and notes.
- Rating/quality signals.
- Contribution/passport metadata for export.

BonzAI+ is the contribution capture layer of the BonzAI economy.
