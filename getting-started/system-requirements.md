# Hardware & Model Choices

BonzAI runs AI on your device. A more powerful computer can use larger models or finish media generation faster, but modest computers can still use smaller models and browser features.

## The simple rule

- **8 GB memory:** start with small chat models and lighter browser workflows.
- **16 GB memory:** comfortable everyday chat, lighter image/audio work, and more model choice.
- **24–32 GB memory:** larger language models, stronger image workflows, and better multitasking.
- **High-end Apple Silicon or a dedicated NVIDIA GPU:** best for large models, video, training, and high-resolution media.

## Storage

Models can be much larger than the application.

- Keep at least 10 GB free for a basic setup.
- Keep 50 GB or more free if you want several language and media models.
- Video, training checkpoints, and generation history can use additional space.

BonzAI shows download size before or during model installation. You can remove models you no longer use.

## Choosing a language model

| Your priority | Choose |
| --- | --- |
| Fast answers and low memory use | Small model |
| Everyday quality | Medium model |
| Difficult reasoning or long writing | Larger model that fits your hardware |
| Programming | A coder-focused model |
| Unrestricted local experimentation | A compatible abliterated model, where lawful |

Quantization reduces model size. Lower-bit versions use less memory and usually run faster, but may lose some accuracy. BonzAI's recommendations are designed to make this tradeoff understandable.

## Choosing media settings

- Begin with SD or HD image resolution.
- Use Turbo/Fast while exploring ideas.
- Switch to higher quality once the prompt is working.
- Generate shorter videos before committing to long clips.
- Close unused large models before training or video generation.

## Apple, NVIDIA, and CPU-only devices

BonzAI selects compatible acceleration when available:

- Apple Silicon uses unified memory and Apple GPU acceleration.
- NVIDIA systems use CUDA-capable paths where supported.
- Other systems can use CPU or available fallback acceleration, but large media models may be slow.

The app's hardware information helps you choose; you do not need to configure acceleration manually.
