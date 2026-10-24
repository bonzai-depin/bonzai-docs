# Web3 Guide: from private work to public ownership

You can use BonzAI for local chat, generation, Roleplay and Smart Workflows without a wallet. This guide is for the moments when you choose to publish something, establish onchain ownership, use a market or pay for a remote service.

These walkthroughs follow all 15 activities in Desktop’s **Web3 Guide**, reviewed against the current source on 24 October 2026. The installed app and selected contracts show the final available actions and amounts. **Configured does not mean deployed:** an address or screen alone is not proof of a working service, funded reward pool or liquid market.

## Before you start

- **Save locally** keeps your work on this device. Back it up yourself.
- **Upload** publishes selected files to storage. You can upload without minting.
- **Mint** creates an onchain token referencing metadata; that metadata may include your prompt.
- **Stake** commits BONZAI under the vault’s withdrawal rules. It does not pay for local inference.
- **Approve** grants a contract permission to spend the displayed token allowance. It is distinct from the following transaction.
- **Gas** is the network fee paid in its native currency. It is separate from a mint fee, trade quote or job price.
- **Claim / withdraw** moves an eligible balance to your wallet. A displayed estimate or local activity record is not a confirmed payout.

Check the network and account shown by the app, the contract involved, the exact amount and recipient, and what will become public. Never put a wallet recovery phrase or private key into a prompt, agent brief or public metadata.

## Choose an outcome

- [Connect Your Wallet](#connect-your-wallet)
- [Decentralized Storage](#decentralized-storage)
- [Tokenize Content](#tokenize-content)
- [Stake BONZAI](#stake-bonzai)
- [Claim Staking Rewards](#claim-staking-rewards)
- [Claim Epoch Pool Rewards](#claim-epoch-pool-rewards)
- [Discover & Trade Tokens](#discover--trade-tokens)
- [Issue an Agent Token](#issue-an-agent-token)
- [Issue a Model Token](#issue-a-model-token)
- [Issue a Game Token](#issue-a-game-token)
- [Collect Trading Fees](#collect-trading-fees)
- [Pay for Remote Workflows](#pay-for-remote-workflows)
- [Earn as an Inference Provider](#earn-as-an-inference-provider)
- [Publish Datasets & Attribution](#publish-datasets--attribution)
- [Use Smart Workflows](#use-smart-workflows)

## Connect Your Wallet

1. Choose Connect in the sidebar and select your wallet.
2. Use the economy network shown here. Keep its native currency for transaction fees.
3. Check the account, network, amount and recipient in your wallet before signing.

**What it costs:** Connecting does not transfer funds. Transactions may require gas; approvals authorize a contract to spend the displayed token amount.

**What you get:** Your wallet signs actions; local creation remains available without it.

## Decentralized Storage

1. Set up your own Pinata JWT below. Desktop stores it encrypted; Web keeps it only for this tab.
2. Choose the file and review its name, type and size. Confirm that you want it public.
3. Upload and keep the IPFS URI / CID. Maintain pinning in your Pinata account for continued availability.

**What it costs:** Your Pinata plan covers storage. No wallet, BONZAI stake or NFT purchase is required.

**What you get:** A public file and a content address. IPFS is not a permanent-storage guarantee; removing a pin cannot delete copies held elsewhere.

## Tokenize Content

1. Open a saved generation and choose Tokenize. Review the original file, title, prompt, model and publishing rights.
2. Connect, configure storage, and stake the required level: text LVL1, audio LVL2, images LVL3, video LVL4, 3D LVL5, training LVL6.
3. Confirm public upload, then create your collection if needed and confirm the mint in your wallet. Keep the receipt.

**What it costs:** BONZAI stays staked. The mint fee and gas are paid in the network’s native currency; the wallet shows the actual contract fee.

**What you get:** An NFT referencing public content and metadata, including the prompt. Marketplace discoverability does not list it for sale or make it private when disabled. Allow as training material permits references to the generation as training material; it does not guarantee revenue. Displayed prices are estimates; your wallet shows the final amount and network fees.

## Stake BONZAI

1. Open Rewards and choose a level or enter a BONZAI amount.
2. Review your new total and withdrawal notice. Approve the token allowance if requested, then confirm the stake.
3. Use Manage membership to request withdrawal. Future rewards stop then; withdraw after the notice and any existing lock expire.

**What it costs:** BONZAI is locked in the staking vault; gas is separate. The reward notice is read from the contract (90 days by default).

**What you get:** Publishing access and participation in reward allocations. Rewards depend on collected fees and eligible stake, not a guaranteed return.

## Claim Staking Rewards

1. Open Rewards → Your share of the activity.
2. Browse closed periods and currencies. Refresh to read your wallet’s claimable balance.
3. Claim each currency in your wallet. Use Earlier to find older periods; leaving the stake does not remove accrued claims.

**What it costs:** Gas for each claim. Rewards stay in their original currency; no automatic swap is performed.

**What you get:** Confirmed rewards transferred directly to your wallet. Trading fees and provider earnings are separate.

## Claim Epoch Pool Rewards

1. Open Rewards → Epoch Pool Rewards.
2. Register eligible locked stake in the current epoch before it closes. This registration is separate from staking-basket membership.
3. After finalization, select an eligible pool, confirm the claim, wait the required block gap, then claim. Skill owners can also check their separate accrued revenue here.

**What it costs:** Gas for registration, confirmation and claims. Eligibility and pool funding are read from the contracts.

**What you get:** A native-currency payout for that registered epoch. It is not the same balance as provider rewards or basket currencies.

## Discover & Trade Tokens

1. Open Markets and select a token to inspect its collection, token address, pool and available price evidence.
2. Use its Trade link only after checking the network and token address in the external exchange.
3. Review the exchange quote, allowance, slippage and gas in your wallet. A missing price is not a zero valuation.

**What it costs:** The exchange quote, pool trading fee and gas. BonzAI does not automatically buy tokens while you browse.

**What you get:** Tokens in your wallet. An indexed asset is not an NFT sale listing or a promise of a liquid market.

**Availability and limits:** Trading needs deployed pools and a compatible exchange on the configured network. Prices and indexing may be unavailable.

## Issue an Agent Token

1. Create a Smart Agent locally. Connect your wallet. Review a new slot purchase, or find and attach an unissued slot you already own.
2. Review and publish its portrait, profile and execution wallet to public storage and the chain.
3. Review the NVDA quote and slippage, then launch the token and locked pool using the slot’s reserve. Identity is locked after issuance.

**What it costs:** The successor slot contract charges 2 ETH per slot: 1 ETH proceeds and 1 ETH reserved liquidity, plus gas. Token issuance uses that reserve.

**What you get:** An agent NFT, its execution identity and social token. Owning social tokens alone does not grant a right to fee payouts.

**Availability and limits:** Scheduled slot sales require a configured active mint window. External marketplace drop support is unverified.

## Issue a Model Token

1. Train a supported checkpoint or LoRA in Tune, or create an abliteration in Uncensor. Validate the result.
2. Mint the training manifest at LVL6. A manifest does not automatically upload your model weights.
3. Set the token profile and liquidity, launch it, then confirm the contributor allocation. Complete a pending allocation separately if that transaction fails.

**What it costs:** Mint fee, gas and the factory’s minimum native liquidity. Liquidity principal stays permanently locked.

**What you get:** A model token and locked pool. The 70% creator allocation can be assigned to contributors; metadata alone does not pay them.

## Issue a Game Token

1. Create and save a game in 3D.
2. Mint its collectible, then choose game token issuance from the mint result.
3. Review the game manifest, token name, symbol and locked liquidity; confirm registration and issuance.

**What it costs:** Mint fee, gas and the factory’s minimum native liquidity (0.01 ETH by default). Principal cannot be withdrawn.

**What you get:** A registered game collectible, token and locked liquidity position.

## Collect Trading Fees

1. In Markets, select your issued agent, model or game token and open Trading fees.
2. Collect pool fees to credit the beneficiaries. Anyone may trigger collection; the collector does not receive all fees.
3. Claim my fees for each currency. Deposit rewards forwards the reward allocation to the staking basket.

**What it costs:** 1% trading fee. Agents: 35% execution wallet / 35% NFT owner / 20% treasury / 10% rewards. Models and games: 70% creator / 20% treasury / 10% rewards.

**What you get:** Only fee income is distributed. Principal remains in the immutable vault; credited balances stay with the original recipient.

## Pay for Remote Workflows

1. Choose a remote Smart Agent and review the outcome, price, payment token, worker, fees and deadlines.
2. Pay in its social token, or choose USDC when conversion is configured. Review the quote and allowance before funding escrow, then send the agreed brief to the provider peer.
3. The agent accepts, works and submits evidence. Review before approving payment, or dispute within the deadline. Refunds and settled earnings require withdrawal.

**What it costs:** The specific agent’s social token plus gas. Workflow prices and fee deductions are part of the reviewed quote.

**What you get:** Escrow separates funding, delivery, settlement and withdrawal. It is separate from trading fees. Local workflows are free.

**Availability and limits:** USDC conversion requires a configured router and available liquidity. Do not send stablecoins directly to the social-token escrow.

## Earn as an Inference Provider

1. Open Network settings → Provider. Choose the pipelines you can serve and review which requests leave the consumer’s device.
2. Serve requests and inspect the Service Time ledger. Local timing records are not proof of onchain earnings.
3. Only independently verified receipts can establish pool entitlement. Claims require a finalized period and unpaused provider claims. Previously earned rewards survive unstaking.

**What it costs:** Provider pool shares depend on verified service time and available pool funding; there is no guaranteed hourly payment.

**What you get:** Pool earnings for generation service. Remote workflow earnings instead go through the owned agent and its job escrow.

**Availability and limits:** An independent attestation service and funded end-to-end settlement must be validated before provider rewards can launch.

## Publish Datasets & Attribution

1. Create a dataset from your own content and verify publication and training permissions.
2. Review exactly what will be shared. Local origin notes are not automatically uploaded or registered.
3. For trained models, review contributor wallets and explicitly register the revenue allocation after issuance.

**What it costs:** Storage plan, registration gas and any publishing requirements shown in the selected flow.

**What you get:** Traceable attribution. A listed contribution or dataset does not by itself create a paid entitlement.

**Availability and limits:** Claim model trading shares in Markets and known workflow-token royalties in Smart-agent jobs. General native-currency revenue-route claims and route discovery do not yet have a dedicated screen.

## Use Smart Workflows

1. Explore templates and choose your desired result.
2. Create a team, add your inputs and configure its shared connectors.
3. Run a task and keep its results. Review and approve a separate quote when hiring a remote agent.

**What it costs:** Local workflows are free. Remote services and optional onchain actions require separate payments.

**What you get:** A local workspace with no license purchase or activation to restore.

## If an action is unavailable or interrupted

A missing contract, storage credential, provider, quote or pool is a prerequisite failure; do not treat it as a completed transaction. Complete the missing setup or keep working locally.

If your wallet submitted a transaction, inspect its status before retrying. Keep the transaction hash, public storage URI and any job or collection identifier. An upload can succeed even if a later mint fails; a completed mint does not prove a later token issuance or allocation succeeded.

Local jobs, escrow payments, trading fees, staking baskets and epoch claims are different balances. Use the section for the action you actually performed rather than assuming one success settles them all.

**Continue:** [Staking](staking-architecture.md) · [Rewards](reward-structure.md) · [Markets](token-markets.md) · [Provider limitations](../p2p-network/provider-guide.md)
