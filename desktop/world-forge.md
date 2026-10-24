# World Forge: build a playable world

World Forge connects generated 3D objects and levels with game assembly and playtesting. Start small: one environment, one useful object and a clear objective for the player.

## From idea to playtest

1. Open **3D** and use **Generate** to make an **Object**. Add a reference image when the selected workflow supports it.
2. Generate a **Level** and save both results to history.
3. Open **Build** once you have a level and object available. Choose the starting level, select its objects and describe the gameplay.
4. Place objects from the palette, then inspect their role, position and interactions.
5. Define a goal the player can complete, such as reaching a destination or collecting objects. Use the director to revise the scene.
6. Playtest, check how the level completes and save a version you want to keep. Add further levels only after the first works.

Generated code and scenes can need iteration. Keep a working version before major revisions. Use the [3D manual](3d.md) for the broader generation workflow.

## Reuse your work

An object can become scenery, a collectible or an obstacle in different places. Keeping reusable objects and levels lets you improve the game without regenerating everything. A project’s manifest describes its components and their relationships.

Where available, companion playtesting uses the game runtime to pursue supported objectives. It does not grant access to your wallet or authorize a publication transaction.

## Publish only when ready

Local creation, assembly and playtesting do not require minting. Publishing a collectible and issuing a game token are optional onchain actions with separate prerequisites and costs.

The current guide describes minting a game collectible, reviewing and registering its manifest, then issuing a token with locked liquidity through configured contracts. This requires a deployed registry, factory and supported market infrastructure. Keep local backups; an onchain manifest is not a backup of all private project data.

[Game token walkthrough](../web3/guide.md#issue-a-game-token) · [Saving versus minting](../web3/guide.md#before-you-start)
