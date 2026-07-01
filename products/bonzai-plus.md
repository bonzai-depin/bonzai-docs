# BonzAI+ Browser Assistant

BonzAI+ turns the current webpage into useful private AI context. It lives in the browser side panel and separates four clear activities: Chat, Dataset, Live, and Imagine.

## The four modes

| Mode | Use it when |
| --- | --- |
| **Chat** | You want a normal conversation or want to ask about captured text/image content |
| **Dataset** | You want to turn a text or image target into a well-described training record |
| **Live** | You want a timestamped account of a video or shared screen as its story unfolds |
| **Imagine** | You want to generate and download images locally in the browser |

Each mode has its own interface. Chat does not show dataset fields, and Dataset does not show free-chat messages.

## Local models and caching

BonzAI+ downloads models when a feature first needs them. Downloads are cached in browser storage. The interface shows stable progress without exposing internal model names.

The browser may remove cached data under storage pressure, after site/extension data is cleared, or in temporary browsing sessions.

## Capture overlay

When Overlay is enabled, a **BonzAI+** button appears over capturable page text and images. It is centered over the target. Click it to make that content the active target.

Turn Overlay off from the extension header when you do not want capture controls on webpages.

## Private by design

Chat, analysis, generation, and curation use local browser models. Prompts and images are not sent to a remote AI service. Normal page access and explicitly configured external links still behave like normal internet activity.

Continue with:

- [Chat Mode](../bonzai-plus/chat.md)
- [Dataset Mode](../bonzai-plus/dataset.md)
- [Live Mode](../bonzai-plus/live.md)
- [Imagine Mode](../bonzai-plus/imagine.md)
