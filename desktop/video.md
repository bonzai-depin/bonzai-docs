# Video Generation

Video mode creates a short video from text or animates a starting image.

## Text to video

1. Describe the scene, subject movement, camera movement, lighting, and ending state.
2. Choose size, duration/frame settings, and quality available to your hardware.
3. Generate a short test.
4. Refine motion language before increasing length or resolution.

## Image to video

Provide a clear source image, then describe what should move and what should stay stable.

Example:

> The camera slowly pushes toward the greenhouse. Rain runs down the glass; leaves move gently in the wind. Keep the building geometry and warm interior lights stable.

## Better motion prompts

- Use one main camera action.
- Describe movement in chronological order.
- Avoid asking every object to move differently.
- State what must remain unchanged.
- Prefer short coherent shots over long multi-scene prompts.

Video generation is among the heaviest local workflows. Lower resolution and shorter clips are the best diagnostic settings when generation is slow or fails.
