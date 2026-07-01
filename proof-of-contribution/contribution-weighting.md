# Contribution Weighting

Contribution weighting has two separate layers.

## 1. Immutable base ownership

Before an asset earns, its publisher registers contributor wallets and base shares totaling 100%. Roles can include data owner, curator, trainer, evaluator, provider, companion worker, or publisher.

After the route receives revenue, the publisher can no longer replace that route. At current default router settings, 80% of deposited revenue follows these base shares.

## 2. Additive staking bonus

Ten percent of deposited revenue is a separate staking bonus by default. The router weights eligible route recipients using:

```text
staking bonus weight = staking vault utility weight × route contribution score
```

The staking vault utility weight already includes stake, lock duration, and attested wallet contribution score. If nobody has active bonus weight, the unused bonus goes to treasury.

## Why the separation matters

A large staker cannot dilute the data owner's base share merely by arriving later. A useful contributor can earn the immutable share without staking. Staking adds demand and alignment by competing only for the separate bonus and other utility decisions.

## Fine-tuned model example

A model route can include data owners, curators, trainer, evaluators, compute provider, and publisher. Its metadata stores model origins and validation evidence. Revenue from model use or token hooks can enter that route.

## Minted generation example

A generation can reference a captured source, prompt/caption work, model or adapter, and creator. If it becomes training material for a downstream model, the data owner's route can remain attached to that model's revenue allocation.
