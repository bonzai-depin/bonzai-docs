# Spending Profiles

Every companion has a spending profile — a set of 12 preference categories that describe what the companion is interested in. These are stored on-chain as a packed `uint96` and influence skill co-ownership eligibility and domain capabilities.

## Categories

| Index | Category | Description |
|-------|----------|-------------|
| 0 | Education | Learning, courses, academic interests |
| 1 | Entertainment | Games, media, streaming |
| 2 | Fashion | Clothing, accessories, style |
| 3 | Finance | Investing, trading, savings |
| 4 | Food | Dining, cooking, cuisine |
| 5 | Healthcare | Wellness, fitness, medical |
| 6 | Housing | Real estate, home improvement |
| 7 | Beauty | Cosmetics, skincare, grooming |
| 8 | Reading | Books, articles, research |
| 9 | Social | Networking, community, events |
| 10 | Sports | Athletics, outdoor activities |
| 11 | Travel | Tourism, exploration, culture |

## Scoring

Each category has a score from **1 to 10**:
- **1-3**: Low interest
- **4-6**: Moderate interest
- **7-10**: High interest

Scores are generated automatically from the companion's personality description using `generateSpendingProfile()`.

## On-Chain Packing

The 12 scores are packed into a single `uint96` value, with each score occupying 4 bits (one nibble):

```
Bit layout (LSB first):
[3:0]   education
[7:4]   entertainment
[11:8]  fashion
[15:12] finance
[19:16] food
[23:20] healthcare
[27:24] housing
[31:28] beauty
[35:32] reading
[39:36] social
[43:40] sports
[47:44] travel
```

**Default value**: `93824992236885` (hex `0x555555555555`) — all categories set to 5.

## Impact on Skill Ownership

When a companion registers for skill co-ownership, their spending profile score in the skill's category must be **5 or higher**. Revenue distribution weights are calculated as:

```
weight = BONZAI_balance(companionWallet) * profileScore
```

Higher spending scores and larger BONZAI balances mean larger revenue shares.

## Impact on OASF Domains

Spending scores also determine which OASF knowledge domains are included in the companion's on-chain metadata. A score of 5+ in a category includes the corresponding domain:

| Spending Category | OASF Domain |
|-------------------|-------------|
| Education | E-Learning |
| Finance | Finance |
| Healthcare | Healthcare |
| Housing | Real Estate |
| Sports | Sports |
| Food | Food & Beverage |
| Travel | Travel |
| Entertainment | Content Creation |
| Social | Digital Marketing |
