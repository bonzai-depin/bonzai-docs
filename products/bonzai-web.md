# BonzAI Web

[BonzAI Web](https://bonzai.sh) lets you try local text AI in your browser and discover the rest of the BonzAI workspace. It is useful for writing, explaining, brainstorming and summarizing text you provide.

## Your first conversation

1. Open Web in a compatible desktop browser.
2. Close the introduction with **Chat Now**.
3. Complete **First-time setup** and download the recommended model. Keep the tab open until it finishes.
4. Wait for the model to be ready, then type your request and send it.
5. Refine the result with a follow-up instruction.

Try: “Turn these notes into a short email. Keep the facts, remove repetition, and end with the next step: …”

The current Web chat flow does not require a wallet or a minimum BONZAI balance. Buying tokens is separate from running the model on your device.

## Models and storage

The model picker shows available models, download controls and an estimated device memory budget. A larger model may be slower or fail to fit. Start with the recommended model, and move down in size if loading or generation fails.

Models are cached in browser storage. Clearing site data, private browsing or browser eviction can remove them. Saved setup preferences are not a backup of your model files.

The sidebar includes prepared product questions as well as conversations created during the session. The current Web implementation keeps live conversation content in memory: do not rely on a reload to preserve it. Copy important answers before closing the page. The history export control currently directs you to Desktop rather than exporting a Web archive.

## Themes and language

Click the theme name in the sidebar to open the gallery. Search by name or filter light/dark palettes, then click a preview. Arrow controls cycle themes. The choice stays in this browser when local storage is available.

Web supports English, French, Spanish, Japanese, Korean, Chinese and Russian. Language and theme preferences are local to this browser; they do not automatically synchronize with Desktop.

## Which tools run here?

Text chat runs in the browser. Image, audio, video, 3D, Roleplay, Smart Workflows and training navigation entries open the Desktop download panel. They describe what Desktop can do; selecting one does not install or run a Desktop model in Web.

The download panel lists Desktop 4.1.0 for Apple Silicon macOS, Windows x64 and Linux amd64 CUDA/ROCm, with sizes and checksum links. You can also share the installation-guide link to another device. [Choose an installer](../getting-started/install-desktop.md).

BonzAI+ is presented separately and its installation is currently marked Coming Soon in Web. Check the [extension guide](../getting-started/install-bonzai-plus.md) for distribution details.

## Privacy and compatibility

Local inference processes prompts on your device. Model downloads and optional wallet, exchange or external documentation links still contact their respective services. Choosing a local model does not grant access to your other tabs or local files.

Browser capabilities, memory and available storage determine whether a model can run. When local inference is unavailable, Web shows an explanation and a route to Desktop; it does not silently send the conversation to a cloud fallback. On mobile, use the download/share links to continue on a supported computer.

**Next:** [Desktop manual](bonzai-desktop.md) · [Web3 Guide](../web3/guide.md) · [Troubleshooting](../reference/troubleshooting.md)
