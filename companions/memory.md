# Companion Memory

BonzAI memory is a local connected knowledge system inspired by Karpathy's LLM Wiki, Obsidian, and Zettelkasten.

It is not merely a transcript. Useful facts become small notes with source, scope, type, timestamps, tags, and relationships.

## Current storage

Desktop stores memory in its local SQL data layer. Existing legacy graph data is migrated lazily into the SQL memory graph and removed from the old store after successful persistence.

## Memory scopes

| Scope | Purpose |
| --- | --- |
| User | Preferences and useful generation/use history belonging to the person |
| Companion identity | Stable character and professional knowledge belonging to one companion |
| Team role | How that companion works inside one specific business team |
| Job | Terms, context, evidence, and lessons for one engagement |
| Source/conversation | Material tied to a particular ingest or active exchange |

Scopes prevent one companion or client context from automatically leaking into another.

## Recall

BonzAI combines:

- lexical search for exact words, names, and phrases;
- local embeddings for semantically related notes;
- scope and recency information;
- graph relationships between sources, people, tasks, decisions, and outputs.

Only relevant notes are assembled into model context. The complete memory archive is not pasted into every prompt.

## What enriches memory

- companion conversations;
- user generation/use history;
- team role instructions and approved work;
- accepted job terms and milestone evidence;
- dataset/training provenance;
- explicit facts and preferences worth retaining.

## Memory graph

Open **Help → Memory** to explore the knowledge graph. Nodes identify their content without requiring a blind click. You can navigate relationships, focus a node, and use the full-screen graph view.

The graph is a navigation tool, not proof that two ideas are causally related. Inspect source and note content before relying on a connection.

## Obsidian/Zettelkasten compatibility

The memory service can represent the graph as an Obsidian-style Markdown vault with links and front matter. This keeps the knowledge portable and human-readable rather than trapping it in a proprietary chat history.

## Memory and reinforcement learning

Memory provides the raw structure needed for later evaluation or reinforcement learning: input, context, action, outcome, evidence, and human approval. BonzAI does not automatically treat every remembered event as a positive training example. Only reviewed, licensed, and appropriately scoped records belong in a training dataset.

## Privacy

Memory remains local by default. Onchain companion identity contains public metadata and wallet links, not private memory content. Publishing a proof or contribution should use hashes and selected metadata rather than exposing the full vault.
