# System Requirements

BonzAI runs AI models locally on your hardware. The requirements depend on which models you want to use.

## Minimum Requirements

- **OS**: macOS 12+ (Apple Silicon or Intel)
- **RAM**: 8 GB
- **Storage**: 5 GB for app + models (varies by model)
- **Node.js**: v20 LTS (for development builds)
- **Python**: 3.10+ (for ML inference server)

## Recommended for Full Experience

- **RAM**: 16 GB+
- **GPU**: Apple Silicon (M1/M2/M3/M4) with unified memory, or NVIDIA GPU with 6+ GB VRAM
- **Storage**: 50 GB+ (for multiple models)

## Model VRAM Requirements

### LLM Models (via OpenClaw)

| Model | Size | VRAM Required |
|-------|------|---------------|
| DeepSeek R1 1.5B | 1.1 GB | 2 GB |
| Gemma 3 1B | 0.8 GB | 2 GB |
| Phi-3 Mini | 2.4 GB | 4 GB |
| Phi-4 Mini | 2.5 GB | 4 GB |
| Qwen 2.5 3B | 2 GB | 4 GB |
| LLaMA 2 7B | 4 GB | 6 GB |
| LLaMA 3.1 8B | 5 GB | 6 GB |
| Mistral 7B | 4.4 GB | 6 GB |
| DeepSeek R1 7B | 4.7 GB | 6 GB |
| GLM-4 7B Flash | 4.7 GB | 6 GB |
| Qwen Coder 7B | 4.7 GB | 6 GB |
| Yi Coder 9B | 5.5 GB | 8 GB |
| MythoMax 13B | 7.9 GB | 10 GB |
| Hermes 4 14B | 9 GB | 10 GB |
| Qwen Coder 14B | 9 GB | 12 GB |
| Codestral 22B | 13 GB | 16 GB |
| GPT-OSS 20B | 12 GB | 14 GB |
| DeepSeek R1 32B | 19 GB | 24 GB |
| Qwen Coder 32B | 19 GB | 24 GB |
| Qwen3 Coder 30B | 18 GB | 24 GB |

### Image, Audio, Video Pipelines (via Flask)

| Pipeline | Approx. VRAM |
|----------|-------------|
| Image Turbo (FLUX Klein) | 8 GB |
| Image Standard (SDXL) | 6 GB |
| Image Quality (FLUX Krea) | 12 GB |
| Image Advanced (Z-Image) | 8 GB |
| Audio Turbo (Kokoro TTS) | 2 GB |
| Audio Quality (Qwen3-TTS) | 4 GB |
| Music (ACE-Step) | 6 GB |
| Video (LTX-2) | 10 GB |
| Vision (Qwen3-VL) | 6 GB |

## Port Configuration

BonzAI uses the following local ports:

| Service | Port | Environment Variable |
|---------|------|---------------------|
| Flask ML Server | 65000 | `BONZAI_SERVER_PORT` |
| OpenClaw LLM | 3002 | `OPENCLAW_API_PORT` |
| OpenClaw Gateway | 18789 | — |
