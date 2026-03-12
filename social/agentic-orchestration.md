# Agentic Orchestration

BonzAI supports two orchestration backends that extend companion capabilities beyond the desktop app: **OpenClaw** and **Hermes Agent**.

## OpenClaw

OpenClaw runs on port 3002 and provides:

- OpenAI-compatible LLM API (`/v1/chat/completions`)
- Multi-channel webhook gateway (port 18789)
- SKILL.md-based skill system

### Configuration

OpenClaw config lives at `~/.openclaw/`. Enable it in **Network Settings > Agentic Orchestration**.

When enabled, BonzAI installs a SKILL.md to `~/.openclaw/skills/ai/bonzai/` that registers all companion commands and pipeline access.

## Hermes Agent

[Hermes Agent](https://hermes-agent.nousresearch.com/docs/) by Nous Research is an alternative orchestrator with similar capabilities.

### Configuration

Hermes config lives at `~/.hermes/`. Enable it in **Network Settings > Agentic Orchestration**.

When enabled, BonzAI:

1. Installs a SKILL.md to `~/.hermes/skills/ai/bonzai/`
2. Adds environment variables to `~/.hermes/.env`:
   - `BONZAI_API_PORT` — Flask server port
   - `BONZAI_LLM_PORT` — OpenClaw LLM port
   - `BONZAI_SKILLS_ENABLED` — Enabled skill list

### SKILL.md

The installed SKILL.md provides Hermes/OpenClaw with:

- All 21 LLM model endpoints
- Image, audio, video, and vision pipeline access
- Companion management commands
- Webhook command routing

## Enabling

Both orchestrators can be toggled independently in **Network Settings > Agentic Orchestration**. They run side by side without conflict.

The self-test in Network Settings verifies that at least one orchestrator is enabled and reachable.
