# Private Inference

BonzAI private inference is the direction for routing work across multiple peers without giving one provider the full prompt/output. It is based on pipeline parallelism and tensor/RPC routing rather than a normal single-provider request.

## Why It Exists

Single-provider P2P is useful, but the provider can see the request. Private inference aims to split work so that peers process only partial tensor operations.

## Conceptual Flow

```text
user device
-> keeps tokenizer, embeddings, sampling, and privacy boundary layers
-> sends intermediate tensor operations to selected peers
-> receives tensor results
-> completes decoding locally
```

## What Stays Local

- Prompt text.
- Token IDs.
- Tokenizer.
- Embedding/unembedding where configured.
- Sampling and detokenization.
- Final output text.

## What Peers See

- Tensor shapes.
- Timing.
- Opaque intermediate operations.
- Model architecture-level information that may already be public.

## Tradeoffs

Private inference is more complex than local or single-provider inference:

- It can be slower.
- It requires compatible models and providers.
- It needs stable peer connectivity.
- It may still leak metadata such as timing and tensor sizes.

## Provider Rewards

Private/sharded providers should be documented under the same provider reward model as other providers unless a product UI explicitly enables a different payment path:

```text
provider seconds / total provider seconds * provider-side pool amount
```

Do not describe private inference as automatically earning ETH/USDC per session unless that payment mode is active in the product.
