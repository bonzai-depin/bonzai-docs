# Capture, Privacy & Troubleshooting

## Capture does not appear

- Confirm Overlay is enabled.
- Reload tabs that were open before BonzAI+ was installed or updated.
- Some browser/internal pages do not allow extension scripts.
- Cross-origin or protected media may prevent direct image extraction.

## Capture stops after changing modes

The target belongs to Chat/Dataset context, while Live owns a separate screen capture. Stop Live before selecting a new page target. If the page changed substantially, capture the target again.

## Old information appears at launch

Transient targets and conversations should start clean unless intentionally restored. Saved dataset records and image history remain available until removed. Clear the relevant history if you do not want it retained.

## Model downloads again

Browser storage may have been cleared, storage pressure may have evicted cached weights, or temporary/private browsing may be in use. Use normal browsing and allow sufficient storage.

## Privacy boundary

The extension's AI work is local. Capturing a page still means BonzAI+ reads the target you select. Live reads the tab/window/screen you explicitly share. Stop sharing when finished.

## Protected video

Some streaming services use protected playback that prevents meaningful frame capture. BonzAI+ cannot bypass browser DRM or site security controls.
