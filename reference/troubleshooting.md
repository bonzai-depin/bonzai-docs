# Troubleshooting

## A model keeps downloading

Check free storage, avoid private browsing, and do not clear BonzAI/browser data. Browser caches can be evicted under storage pressure.

## Desktop takes a long time to open

BonzAI starts local services and inspects model/hardware state. Large eager imports or loading model history during startup can add delay. Wait for Ready before starting a generation; report repeated delays with logs and hardware information.

## Generation is out of memory

Choose a smaller model, lower media resolution, stop another active pipeline, and close memory-heavy applications.

## Connector says authentication is needed

Open Company → Connectors, add or refresh the credential, test it, and confirm the account/realm identifier. Grant only the required team access.

## Wallet action is unavailable

Confirm the wallet is connected to the configured network and that the release contains a deployed contract address. Local-only features continue working without it.

## BonzAI+ capture is missing

Enable Overlay and reload a tab opened before extension installation. Browser-internal, protected, and some cross-origin pages cannot be captured.

## Live misses an event

Use the correct shared tab, verify the video timestamp is moving, choose a more suitable analysis mode/window, and review hardware load. Live is assistive local interpretation, not a guaranteed official event feed.

## Get useful support

Include product/version, operating system, hardware/memory, exact view, selected mode, steps to reproduce, visible status, and the complete error message. Never share a seed phrase or private key.
