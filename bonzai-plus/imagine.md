# Imagine Mode

Imagine generates images privately in the browser using a local WebGPU image engine when supported.

## Generate

1. Choose **Speed** or **Quality**.
2. Choose 128, 256, 512, or 1024 resolution.
3. Enter a prompt.
4. Press Enter or choose **Generate Image**.

Speed and resolution are independent. The default is Speed at 512.

## Progress

The progress area remains a fixed height so the layout does not jump. It shows a status, a full-width progress bar, percentage, and current step such as **Step 2/4**.

## Results

When an image is displayed, you can:

- download it;
- clear it;
- view it in History;
- remove individual history items.

History items use the full panel width, with the image above its prompt and generation metadata.

## Model variants

Speed uses the more compact 1-bit image variant. Quality uses the ternary variant for stronger prompt fidelity and image quality. BonzAI chooses the compatible browser runtime for the current GPU environment; models remain cached locally after download.

## Device support

In-browser image generation requires modern GPU/browser features and substantial memory. If unsupported, BonzAI+ explains the limitation rather than sending the prompt to a remote image service.
