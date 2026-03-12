# Video Generation

BonzAI generates videos locally using the LTX-2 model (GGUF quantized, ~10 GB).

## Endpoint

```
POST http://localhost:65000/video
```

## Modes

- **Text-to-Video**: Generate a video from a text prompt
- **Image-to-Video**: Animate a static image into a video clip

## Request Format

```json
{
  "prompt": "A cat walking in a garden, cinematic lighting",
  "height": 480,
  "width": 768,
  "num_frames": 81,
  "fps": 24,
  "num_inference_steps": 30,
  "guidance_scale": 3.5,
  "image_base64": "..."
}
```

| Parameter | Default | Description |
|-----------|---------|-------------|
| `prompt` | — | Text description of the video |
| `height` | 480 | Video height in pixels |
| `width` | 768 | Video width in pixels |
| `num_frames` | 81 | Number of frames to generate |
| `fps` | 24 | Frames per second |
| `num_inference_steps` | 30 | Denoising steps (higher = better quality, slower) |
| `guidance_scale` | 3.5 | How closely to follow the prompt |
| `image_base64` | — | Optional base64 image for image-to-video mode |

## Companion Video Pipeline

In the roleplay system, companions can generate contextual videos:

1. LLM generates the scene description
2. Optionally, an image is generated first as a keyframe
3. LTX-2 generates the video, conditioned on audio if available

## Minting Video NFTs

Generated videos can be minted on Base. Requires **LVL4** (25,000 BONZAI held).
