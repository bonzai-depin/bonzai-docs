# BonzAI+ Browser Assistant

BonzAI+ is the BonzAI browser extension.

It lives in the browser side panel and helps users work with whatever is on the current page: text, images, videos, comments, articles, product pages, research, references, and prompts.

## What Problem It Solves

The web is full of useful material, but normal AI chat tools make it awkward to collect, describe, clean, and reuse that material.

BonzAI+ turns browsing into structured AI work:

- Ask questions about a page.
- Capture text or images with a BonzAI+ overlay.
- Follow a video and create a live transcript.
- Generate images locally in the browser when supported.
- Turn captured material into dataset records for BonzAI Desktop.

## Modes

| Mode | What the user does |
| --- | --- |
| **Chat** | Ask BonzAI+ questions, with or without a captured target. |
| **Live** | Follow what is happening on screen or in a video and save useful transcript cues. |
| **Imagine** | Generate images privately in the browser. |
| **Dataset** | Capture text/images and turn them into training-ready records. |

## Capture

BonzAI+ can place a **BonzAI+** button over page content. Clicking it sets that text or image as the current target.

From there, the user can:

- Ask questions about the target in Chat.
- Run Smart Analysis in Dataset mode.
- Save tags, captions, source links, ratings, and metadata.
- Export the records to Desktop.

Image records can include base64 image data when available.

## Live

Live mode is for understanding what is happening on screen.

It should not stay silent forever waiting for a perfect OCR event. It should describe the story as it unfolds: scene changes, actions, quotes, score changes, catches, knockouts, goals, product demos, tutorials, gameplay, interviews, and other moments that matter for that video type.

## Imagine

Imagine mode adds browser-local image generation when the device supports it.

It includes:

- Resolution choices.
- Speed/quality choices.
- Progress.
- Image history.
- Clear and download actions.
- Cached models so the user does not download the same model every launch.

## Dataset

Dataset mode is how BonzAI+ becomes useful for training.

A record can include:

- The captured text or image.
- Source URL.
- Page context.
- Title.
- Caption.
- Tags.
- Notes.
- Rating.
- Image data.
- Permission and contribution metadata.

The goal is simple: make it easy to collect high-quality material from the web and bring it into BonzAI Desktop.
