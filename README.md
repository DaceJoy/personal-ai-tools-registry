# personal-ai-tools-registry

Curated registry of tools, infrastructure, and libraries for Personal AI systems.

This is **not** an awesome-list. Every entry is evaluated specifically for use in
[Personal AI](https://github.com/DaceJoy/personal-ai-core-public) deployments:
local-first, multi-tenant, privacy-aware, ARM64-compatible where relevant.

## Categories

| Category | Recommended tool | Phase |
|----------|-----------------|-------|
| [Vector Databases](categories/vector-databases.yaml) | Qdrant | 2 |
| [Document Ingest](categories/document-ingest.yaml) | Docling | 2 |

## How to use

Each tool entry includes:
- `source.docs` — official documentation URL (always present, even without a GitHub repo)
- `install.hint` — quick start command
- `relevance_to_personalai.phase` — when to activate (1=now, 2=multi-user, 3=scale)
- `alternatives` — other tools evaluated for the same use case

## Maintenance

Entries are proposed by `ecosystem-scout` (quarterly) and reviewed by `capability-auditor`
before being added here. See [CONTRIBUTING.md](CONTRIBUTING.md) for the entry format.

`last_verified` dates indicate when each entry was last reviewed against current upstream state.
