# Text Generation

BonzAI supports a broad catalog of local language models plus custom GGUF language models stored on your computer.

## Choose by purpose

- Small general models for fast everyday chat.
- Reasoning models for structured analysis.
- Coder models for programming and technical work.
- Creative/roleplay models for companions and fiction.
- Larger models for difficult instructions when hardware permits.
- Abliterated models for lawful local experimentation with reduced refusal behavior.

Notable current families include Qwen, DeepSeek, Gemma, GLM 4/5, MiniMax M2/M3, Ornith 9B/35B, Hermes, Mistral, Llama, Phi, Codestral, Yi Coder, GPT-OSS, and DiffusionGemma. Exact variants and quants appear in Desktop because the catalog evolves faster than a static list.

## Quantization

Quantization compresses a model. Smaller quants need less memory and run faster; larger quants preserve more quality. BonzAI emphasizes Unsloth-compatible GGUF sources where available and displays hardware guidance.

## Context and recall

Conversation context contains the current exchange. Persistent memory contains selected useful knowledge across time. Keeping them separate prevents every old message from overwhelming every new prompt.

## Custom GGUF

Custom GGUF import is for language models only. The file remains on your storage. Compatibility depends on whether the bundled local inference runtime supports that model architecture.
