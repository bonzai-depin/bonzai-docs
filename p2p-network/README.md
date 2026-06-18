# P2P Network

BonzAI Desktop can run in local, consumer, or provider modes. The P2P network lets users discover machines, route inference, and reward providers through service-time accounting and MintPool provider-side rewards.

## Modes

| Mode | What happens |
| --- | --- |
| Local | Requests run on the user's machine |
| Consumer | Requests can route to selected LAN or remote providers |
| Provider | The user's machine serves inference to others |

## Provider Economy

The current provider economy is based on service time:

1. Providers run BonzAI Desktop in Provider mode.
2. Providers advertise pipelines and peer information.
3. Service time is recorded for eligible providers.
4. Provider-side MintPool rewards are claimed after epochs finalize.

Older x402-style ETH/USDC payment rails may exist in code or future optional flows, but the default docs should explain provider rewards through the MintPool service-time model.

## Pipelines

Providers can advertise support for combinations of:

- LLM/text.
- Image.
- Audio.
- Music.
- Video.
- Vision.
- Private/sharded inference where supported.

## Discovery

Provider discovery can use:

- LAN/mDNS for local network providers.
- Onchain provider registry for remote providers.
- App-level selected provider lists for routing.

## Privacy

Local mode keeps requests on the user's machine. Consumer mode can reveal prompts/content to selected providers unless private/sharded inference is used. Users should select providers intentionally.
