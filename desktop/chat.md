# Chat

Chat is for writing, reasoning, research over supplied context, coding, planning, and everyday questions.

## Start a conversation

1. Open **Create → Chat**.
2. Select a model. The recommended choice balances quality and your available memory.
3. Download it if this is the first use.
4. Type your message and send it.

Press Enter to send. Use a line break when you want a multi-line prompt.

## Choose a model

Model cards explain size, purpose, and estimated hardware needs. Smaller models are faster; larger models can handle more difficult instructions but consume more memory.

You can also import a custom **GGUF language model** stored on your computer. Custom GGUF loading is for LLM chat, not image or video models.

## Context and memory

BonzAI can recall relevant local memory instead of pasting an entire lifetime of notes into every prompt. Recall searches both words and locally computed semantic similarity.

Memory scopes keep context separated:

- user memory for your general preferences and history;
- companion identity memory;
- team-role memory;
- job-specific memory;
- conversation context.

## Conversation history

History lets you return to useful work. Clearing a conversation removes its visible messages; it does not automatically erase every memory note derived from prior work. Use the Memory view when you want to inspect or remove persistent knowledge.

## Better results

- State the outcome, audience, source material, and constraints.
- Ask the model to identify uncertainty rather than invent facts.
- Break very large tasks into stages.
- Use a larger model only when the smaller model genuinely struggles.
- Start a clean conversation when old context is confusing the current task.

## When a response fails

- Retry once.
- Shorten an extremely long prompt.
- Clear unrelated conversation context.
- Confirm the model finished loading.
- Switch to a smaller model if memory pressure is high.
- Open settings/diagnostics if the local model service repeatedly stops.
