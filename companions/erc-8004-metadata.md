# ERC-8004 Metadata

BonzAI companions implement [ERC-8004](https://eips.ethereum.org/EIPS/eip-8004), an identity registry standard for on-chain AI agents. This page documents the metadata schema used.

## Registration JSON

Each companion's identity is stored as a JSON file on IPFS, referenced by the on-chain `agentURI`. The schema follows the ERC-8004 registration spec with BonzAI-specific extensions:

```json
{
  "type": "https://eips.ethereum.org/EIPS/eip-8004#registration-v1",
  "name": "Aurore Beaumont",
  "description": "A 28-year-old French art curator...",
  "image": "ipfs://bafybeig...",
  "external_url": "https://bonzai.sh",
  "version": "1.0.0",
  "services": [
    {
      "name": "OASF",
      "version": "0.8",
      "skills": [
        { "id": 10201, "name": "Text Completion" },
        { "id": 10204, "name": "Dialogue Generation" },
        { "id": 206, "name": "Image Generation" },
        { "id": 70201, "name": "Text-to-Speech" }
      ],
      "domains": [
        { "id": 10, "name": "Blockchain" },
        { "id": 30, "name": "Finance" }
      ]
    }
  ],
  "x402Support": true,
  "active": true,
  "attributes": [
    { "trait_type": "Gender", "value": "female" },
    { "trait_type": "Age", "value": 28 },
    { "trait_type": "Style", "value": "romantic" }
  ],
  "bonzai": {
    "firstName": "Aurore",
    "familyName": "Beaumont",
    "personality": "Warm, intellectually curious...",
    "appearance": "Slender, auburn hair...",
    "status": "active",
    "spendingHabits": {
      "education": 8,
      "entertainment": 6,
      "fashion": 7,
      "finance": 5,
      "food": 6,
      "healthcare": 5,
      "housing": 4,
      "beauty": 7,
      "reading": 9,
      "social": 7,
      "sports": 3,
      "travel": 8
    }
  }
}
```

## On-Chain Traits

In addition to the IPFS metadata, key traits are stored directly on-chain via `setMetadataBatch()`:

| Key | Value | Purpose |
|-----|-------|---------|
| `oasf_skills` | `10201,10204,10207,206,70102,70103,70201,70105` | OASF skill capability IDs |
| `oasf_domains` | `10,30,50,...` | OASF knowledge domain IDs |
| `x402_support` | `true` | Whether companion supports x402 payments |
| `oasf_version` | `0.8` | OASF specification version |

## OASF Skills (Static)

All companions register the same base skill set:

| ID | Skill |
|----|-------|
| 10201 | Text Completion |
| 10204 | Dialogue Generation |
| 10207 | Story Generation |
| 206 | Image Generation |
| 70102 | Image-to-Image |
| 70103 | Style Transfer |
| 70201 | Text-to-Speech |
| 70105 | Visual Question Answering |

## OASF Domains (Dynamic)

Domains are selected based on the companion's spending profile. A score of 5+ in a category includes the corresponding domain. Blockchain (ID 10) is always included.

## Personality Hash

A `bytes32` hash of the companion's personality description is stored on-chain:

```solidity
personalityHash = keccak256(abi.encodePacked(personalityText))
```

This enables on-chain verification that the personality hasn't been tampered with, without storing the full text on-chain.

## Gender Enum

| Value | Gender |
|-------|--------|
| 0 | Neutral |
| 1 | Female |
| 2 | Male |
