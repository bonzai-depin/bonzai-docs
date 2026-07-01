# Inference Modes

BonzAI Desktop has three practical inference modes.

## Mode Summary

| Mode | Role | Request handling |
| --- | --- | --- |
| Local | Self-contained user | Runs on your own machine |
| Consumer | Client | Routes to selected providers when configured |
| Provider | Server | Runs locally and serves other peers |

## Local Mode

Local mode is the default private path. Requests run through your local OpenClaw and Flask backends.

Use local mode when:

- You have the required model downloaded.
- Your device can run the pipeline.
- You want maximum privacy.

## Consumer Mode

Consumer mode routes requests to selected providers.

Provider selection can include:

- LAN providers discovered locally.
- Remote providers discovered through registry paths.
- Multiple selected providers for redundancy.

Consumer mode can expose request content to selected providers unless private/sharded inference is used.

## Provider Mode

Provider mode turns your machine into a serving node. It advertises capabilities and can earn provider-side rewards based on recorded service time.

## Chat And Social Orchestration

Network mode also applies to supported external chat/orchestration requests, which follow the selected provider configuration.
