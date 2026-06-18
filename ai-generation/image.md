# Image Generation

BonzAI offers four image generation pipelines, each optimized for different use cases. All run locally via the Flask server on port 65000.

## Pipelines

| Pipeline | Model | Speed | Quality | VRAM |
|----------|-------|-------|---------|------|
| **Turbo** | FLUX Klein | Fast | Good | 8 GB |
| **Standard** | SDXL + LoRA | Medium | High (uncensored) | 6 GB |
| **Quality** | FLUX Krea | Slow | Best | 12 GB |
| **Advanced** | Z-Image Turbo | Fast | High | 8 GB |

## API Endpoints

### Turbo
```
POST http://localhost:65000/image/turbo
```

### Standard
```
POST http://localhost:65000/image/standard
```

### Quality
```
POST http://localhost:65000/image/quality
```

### Advanced
```
POST http://localhost:65000/image/advanced
```

## Request Format

```json
{
  "prompt": "A cyberpunk cityscape at sunset",
  "negative_prompt": "blurry, low quality",
  "width": 1024,
  "height": 1024,
  "num_inference_steps": 30,
  "guidance_scale": 7.5
}
```

## Companion Portraits

When generating images for companions, BonzAI uses a multi-step pipeline:

1. **GLM Flash** (primary) or **LLaMA** (fallback) enhances the text prompt with visual details
2. The enhanced prompt is sent to the selected image pipeline
3. Generated images stay local unless the user mints, publishes, or explicitly uploads metadata/media

## Minting as NFTs

Generated images can be minted as content NFTs through the configured Desktop minting path. Requires **LVL3** (10,000 BONZAI held) or permanent unlock.

- Image mint fee: 0.0015 ETH unless unlocked
- Metadata/media: IPFS/Pinata or configured IPFS-compatible storage
- LUKSO: Universal Profiles only unless a content contract is explicitly configured
