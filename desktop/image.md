# Image Generation

Image mode creates private images from text prompts. Different modes trade speed, hardware use, style, and fidelity.

## Modes

| Mode | Best use |
| --- | --- |
| **Turbo** | Fast exploration and prompt iteration |
| **Standard** | Flexible SDXL generation and compatible local workflows |
| **Standard+** | Krea 2 Turbo for stronger fidelity with an eight-step workflow |
| **Quality/Advanced** | Higher-fidelity generation when your hardware can support it |
| **Edit** | Transform a supplied starting image |

## Create an image

1. Open **Create → Image**.
2. Choose a generation mode.
3. Choose a resolution.
4. Describe subject, action, composition, light, environment, medium, and mood.
5. Generate.

Use a lower resolution while refining a prompt, then increase it for the final version.

## Krea 2 Standard+

Krea 2 works best at a native high-resolution denoising scale. When you request SD or HD, BonzAI internally renders at an appropriate native scale and returns a sharp downsample at the selected output size. This is slower than denoising directly at SD but avoids soft, blurry results.

## History and downloads

Generated images appear in history with their prompt and settings. You can inspect, download, reuse, remove, or mint an eligible generation. Removing an item from local history is different from deleting an already published asset.

## Prompt recipe

> **Subject and action**, **camera/composition**, **environment**, **lighting**, **material or visual medium**, **mood**, **important exclusions**.

Example:

> A glass greenhouse on a rainy city rooftop, wide establishing shot, wet steel and dense tropical plants, soft overcast daylight with warm lamps inside, cinematic editorial photography, calm and believable, no text or logos.

## Common problems

| Problem | Try |
| --- | --- |
| Image is blurry | Use Standard+ native-scale fix, increase resolution, simplify conflicting style words |
| Subject is wrong | Put the subject/action first and remove vague synonyms |
| Text is malformed | Generate the visual without text, then add typography in a design tool |
| Out of memory | Lower resolution, use Turbo, close another loaded model |
| Download remains visible after completion | Refresh model status; completed models should change to ready without reloading the whole app |
