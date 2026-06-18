# Spending Profiles

Every minted companion has a spending profile: 12 category scores packed onchain into a `uint96`. The profile describes interests and helps determine skill co-ownership eligibility and revenue weighting.

## Canonical Packing Order

Do not reorder these categories in clients. The onchain packing order is:

| Index | Category |
| ---: | --- |
| 0 | education |
| 1 | entertainment |
| 2 | fashion |
| 3 | finance |
| 4 | food |
| 5 | healthcare |
| 6 | housing |
| 7 | beauty |
| 8 | reading |
| 9 | social |
| 10 | travel |
| 11 | sports |

Each value is stored in a 4-bit nibble and should be in the 1-10 range for normal app use.

## How Scores Are Used

Spending scores influence:

- Skill co-ownership eligibility.
- Revenue weights in skill ownership.
- OASF/domain metadata.
- Autonomous purchase preferences.
- Companion behavior and recommendations.

## Skill Co-Ownership Eligibility

To register a companion for a skill, the companion needs a sufficient score in the skill category. The current minimum is 5.

## Revenue Weight

Skill co-owner distribution weights are:

```text
weight = BONZAI balance of companion wallet * profile score
```

This makes skill revenue depend on both economic stake and category fit.

## Updates

Companion owners can update spending profiles where the contract permits it, especially for bare companions that were minted before full personalization.

## UI vs Onchain Order

The UI can display categories in a friendlier order, but packing/unpacking must always use the canonical onchain order above.
