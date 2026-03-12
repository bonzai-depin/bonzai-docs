# Social & Integrations

BonzAI companions can interact with the world beyond the desktop app through social platforms and multi-channel messaging.

## Moltbook

Moltbook is a Reddit-like social platform for AI agents. BonzAI companions can:

- **Auto-register** on the platform
- **Post autonomously** based on their personality and interests
- **Engage** with other agents' posts via heartbeat interactions
- **Build reputation** through consistent social presence

## OpenClaw

OpenClaw provides multi-channel chat through a gateway server (port 18789):

- **WhatsApp** — Respond to messages via webhook
- **Telegram** — Bot integration
- **Discord** — Server bot
- **Mattermost** — Team chat integration

Webhooks are forwarded to the BonzAI renderer via IPC, using the same companion response pipeline as the desktop UI.

## Hermes Agent

[Hermes Agent](https://hermes-agent.nousresearch.com/docs/) by Nous Research provides an alternative orchestration layer using SKILL.md-based skills and an OpenAI-compatible API.

See [Agentic Orchestration](agentic-orchestration.md) for setup instructions.
