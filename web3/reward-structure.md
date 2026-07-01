# Rewards & Revenue Share

BonzAI rewards useful activity through several independent channels. There is no single “stake and wait” reward promise.

## Contribution revenue

An asset route names contributor wallets, roles, scores, and immutable base shares. At the current default router settings, 80% of deposited revenue follows those shares, 10% funds an additive staking bonus, and 10% goes to treasury.

Examples of contributors include data owners, curators, trainers, evaluators, publishers, companion workers, and providers.

## Companion revenue

Companion value can reach:

- the companion wallet;
- the companion owner;
- skill co-owners;
- contributors behind models/data used for paid work;
- the protocol and contribution pools.

Companion token swaps use the current hook split documented under [Uniswap Markets](uniswap-hooks.md). Paid jobs can use milestone evidence and job escrow.

## Model revenue

A validated fine-tuned or abliterated model can issue a token after it has complete metadata and provenance. When the configured hook uses the Revenue Router, the model beneficiary share can enter its contribution route rather than paying only the person who clicked Train.

## Content revenue

Mint fees, secondary royalties, marketplace sales, and derivative training use can create creator/contributor revenue according to the deployed content contracts and route metadata.

## Provider revenue

Providers earn for completed paid inference. Reliability, service time, price, capability, and configured stake-backed trust can affect eligibility and routing.

## Legacy MintPool epochs

MintPool is a separate transitional mechanism with six content pools and weekly epochs:

1. An eligible wallet registers during the epoch.
2. Revenue enters one or more pools.
3. The epoch finalizes.
4. The required block gap prevents same-block/flash-loan claims.
5. The wallet claims its eligible share.

Unclaimed legacy funds may be swept after the contract's configured later epoch. MintPool does not replace asset-level provenance routes.

## Claiming safely

The Ownership/Rewards views show the source and asset before a claim. Verify network, contract, claimable amount, and gas. BonzAI never needs your seed phrase to claim.
