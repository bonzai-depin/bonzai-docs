# Text Generation (LLM)

BonzAI ships with 21 large language models accessible through the GenerativeText interface. All models run locally via OpenClaw on port 3002 using an OpenAI-compatible API.

## Available Models

### Small (2-4 GB VRAM)

| Model | Parameters | Size | Best For |
|-------|-----------|------|----------|
| Gemma 3 1B | 1B | 0.8 GB | Quick responses, low-resource machines |
| DeepSeek R1 1.5B | 1.5B | 1.1 GB | Reasoning on constrained hardware |
| Qwen 2.5 3B | 3B | 2 GB | Balanced quality/speed |
| Phi-3 Mini | 3.8B | 2.4 GB | General purpose |
| Phi-4 Mini | 3.8B | 2.5 GB | Improved Phi-3 successor |

### Medium (6-10 GB VRAM)

| Model | Parameters | Size | Best For |
|-------|-----------|------|----------|
| LLaMA 2 7B | 7B | 4 GB | General chat |
| Mistral 7B | 7B | 4.4 GB | Instruction following |
| DeepSeek R1 7B | 7B | 4.7 GB | Chain-of-thought reasoning |
| GLM-4 7B Flash | 7B | 4.7 GB | Fast bilingual (EN/CN) |
| Qwen Coder 7B | 7B | 4.7 GB | Code generation |
| LLaMA 3.1 8B | 8B | 5 GB | Latest Meta model |
| Yi Coder 9B | 9B | 5.5 GB | Code + general |
| MythoMax 13B | 13B | 7.9 GB | Creative writing, roleplay |
| Hermes 4 14B | 14B | 9 GB | Tool use, function calling |

### Large (12-24 GB VRAM)

| Model | Parameters | Size | Best For |
|-------|-----------|------|----------|
| Qwen Coder 14B | 14B | 9 GB | Advanced code generation |
| GPT-OSS 20B | 20B | 12 GB | Open-source GPT alternative |
| Codestral 22B | 22B | 13 GB | Production-grade coding |
| Qwen3 Coder 30B | 30B | 18 GB | Top-tier code + reasoning |
| DeepSeek R1 32B | 32B | 19 GB | Advanced reasoning |
| Qwen Coder 32B | 32B | 19 GB | Large-scale code projects |

## API Endpoint

All LLM inference uses the OpenAI-compatible endpoint:

```
POST http://localhost:3002/v1/chat/completions
```

Request format:
```json
{
  "model": "model-filename.gguf",
  "messages": [
    { "role": "system", "content": "You are a helpful assistant." },
    { "role": "user", "content": "Hello!" }
  ],
  "temperature": 0.7,
  "max_tokens": 2048
}
```

## Model Downloads

Models are downloaded automatically on first use to `~/bonzai-models/`. All model files use GGUF quantization format for efficient local inference.

**Important**: Model filenames are always lowercase (e.g., `qwen3.5-27b-q2_k.gguf`), even if the download URL uses mixed case.
