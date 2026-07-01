# P2P Network

The P2P network lets one BonzAI Desktop machine serve supported inference to another.

## Modes

| Mode | Meaning |
| --- | --- |
| **Local** | Work runs only on your machine |
| **Consumer** | You deliberately route compatible work to a selected LAN or remote provider |
| **Provider** | Your machine advertises selected pipelines and serves accepted work |

## Discovery

Trusted local providers can be found on the same network. Remote providers use peer information and the configured onchain Provider Registry.

## Payments and rewards

BonzAI contains two real provider mechanisms that may be enabled by release configuration:

- direct x402-style signed ETH payments for paid remote inference, with the configured platform fee;
- provider service-time/MintPool reward accounting where those contracts are deployed.

Staked `$BONZAI` and verified service quality can provide additional trust/routing signals through the v4 contribution economy.

## Privacy

Local mode keeps prompts and inputs on your machine. A normal remote provider may see the work it must process. Use only providers you trust unless a supported private/sharded inference mode explicitly protects that workload.
