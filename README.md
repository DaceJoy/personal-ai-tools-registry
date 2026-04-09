# personal-ai-tools-registry

> [!NOTE]
> This is a **curated registry**, not a generic awesome-list.
> Every entry is evaluated for use in [Personal AI](https://github.com/DaceJoy/personal-ai-core-public) deployments:
> local-first · multi-tenant · privacy-aware · ARM64-compatible.

![Tools](https://img.shields.io/badge/tools-9-blue)
![Categories](https://img.shields.io/badge/categories-13-green)
![Maintained](https://img.shields.io/badge/maintained%20by-ecosystem--scout-orange)

---

> Special thanks to **[Daniel Miessler](https://github.com/danielmiessler)** for the inspiration.
> This registry exists because of his work on [Personal AI Infrastructure](https://github.com/danielmiessler/Personal_AI_Infrastructure).

---

## Contents

- [How to read this registry](#how-to-read-this-registry)
- [Review status](#review-status)
- [🏗️ Agent Frameworks & Architecture](#-agent-frameworks--architecture)
- [🧰 Skill Packs](#-skill-packs)
- [🔒 Security Scanning](#-security-scanning)
- [⚡ Code Context & Token Optimization](#-code-context--token-optimization)
- [🗄️ Vector Databases](#️-vector-databases)
- [📄 Document Ingestion](#-document-ingestion)
- [Adding a tool](#adding-a-tool)

---

## How to read this registry

Each tool lives in `tools/<tool-id>/` with up to three files:

| File | Purpose |
|------|---------|
| `meta.yaml` | Source URLs, install hints, relevance to PersonalAI, phase |
| `categories.yaml` | Detected categories, keywords, use cases |
| `comparison.yaml` | Side-by-side comparison with alternatives (optional) |

**Phase** indicates when a tool becomes relevant:

| Phase | Trigger |
|-------|---------|
| ![Phase 1](https://img.shields.io/badge/phase-1%20now-brightgreen) | Single user, active now |
| ![Phase 2](https://img.shields.io/badge/phase-2%20multi--user-yellow) | Second user or company tenant added |
| ![Phase 3](https://img.shields.io/badge/phase-3%20scale-red) | Hundreds of users, enterprise |

> [!TIP]
> `upstream_fork` entries point to maintained forks. Fork sync is automated monthly.

---

## Review status

> [!NOTE]
> `last_verified` dates are maintained in each `tools/<id>/meta.yaml`.
> ecosystem-scout checks this table to decide which entries need a fresh review.
> Entries not reviewed in **90+ days** are flagged for re-verification.

| Tool | Last verified | Phase | Status |
|------|--------------|-------|--------|
| [PAI](tools/pai/meta.yaml) | 2026-04-09 | 1 | ✅ active |
| [everything-claude-code](tools/everything-claude-code/meta.yaml) | 2026-04-09 | 1 | ✅ active |
| [agentshield](tools/agentshield/meta.yaml) | 2026-04-09 | 1 | ✅ active |
| [code-review-graph](tools/code-review-graph/meta.yaml) | 2026-04-09 | 1 | ✅ active |
| [gstack](tools/gstack/meta.yaml) | 2026-04-09 | 1 | ✅ active |
| [qdrant](tools/qdrant/meta.yaml) | 2026-04-09 | 2 | ✅ active |
| [docling](tools/docling/meta.yaml) | 2026-04-09 | 2 | ✅ active |
| [bge-m3](tools/bge-m3/meta.yaml) | 2026-04-09 | 2 | 👀 watch |

> When running ecosystem-scout manually:
> ```
> 1. Review all entries (regardless of last_verified)
> 2. Review only entries older than 90 days  [default]
> 3. Review selected entries — specify tool IDs
> ```

---

## 🏗️ Agent Frameworks & Architecture

Tools that provide conceptual foundations, architecture patterns, or orchestration models.

### [Personal AI Infrastructure (PAI)](tools/pai/meta.yaml)

![Phase 1](https://img.shields.io/badge/phase-1-brightgreen)
![Adoption](https://img.shields.io/badge/adoption-audit--only-lightgrey)
![Fork](https://img.shields.io/badge/fork-upstream--pai-blue)

Foundation architecture by Daniel Miessler. Conceptual base for this project's
multi-tenant extensions, capability auditor, and interview-driven setup.

- **Source:** https://github.com/danielmiessler/Personal_AI_Infrastructure
- **Use in PersonalAI:** Bootstrap concepts only — `update_policy: audit-only`

---

## 🧰 Skill Packs

Collections of Claude Code skills and specialist roles for selective adoption.

### [Everything Claude Code](tools/everything-claude-code/meta.yaml)

![Phase 1](https://img.shields.io/badge/phase-1-brightgreen)
![Stars](https://img.shields.io/github/stars/affaan-m/everything-claude-code?style=flat)
![Fork](https://img.shields.io/badge/fork-upstream--everything--claude--code-blue)

156 Claude Code skills · 38 agents · AgentShield security scanner.
Adopt selectively via `capability-auditor` — do not import wholesale.

- **Source:** https://github.com/affaan-m/everything-claude-code
- **Keywords:** skills, hooks, memory patterns, AgentShield, slash commands
- **Compare with:** [gstack](tools/gstack/meta.yaml) — specialist roles vs breadth of skills

### [gstack](tools/gstack/meta.yaml)

![Phase 1](https://img.shields.io/badge/phase-1-brightgreen)
![Stars](https://img.shields.io/github/stars/garrytan/gstack?style=flat)
![Fork](https://img.shields.io/badge/fork-upstream--gstack-blue)

23 specialist roles by Garry Tan (YC CEO): CEO · Designer · QA · Security · Release Engineer.
Pattern: activate a specialist role for focused, expert-level responses.

- **Source:** https://github.com/garrytan/gstack
- **Keywords:** specialist skills, virtual team, role-based prompting
- **Compare with:** [everything-claude-code](tools/everything-claude-code/meta.yaml) — depth per role vs breadth

---

## 🔒 Security Scanning

Tools for auditing agent configs, hooks, MCP servers, and detecting secrets or injection risks.

### [AgentShield](tools/agentshield/meta.yaml)

![Phase 1](https://img.shields.io/badge/phase-1-brightgreen)
![OWASP](https://img.shields.io/badge/OWASP-LLM01%20LLM02%20LLM06%20LLM07-red)
![Fork](https://img.shields.io/badge/fork-upstream--agentshield-blue)

102 security rules across 5 categories. Used as a mandatory security gate
before every promotion to `active`.

- **Source:** https://github.com/affaan-m/agentshield
- **Install:** `pip install agentshield` or `uvx agentshield scan .`
- **Covers:** secrets detection · hook injection · MCP security · jailbreak detection

---

## ⚡ Code Context & Token Optimization

Tools that reduce token usage and improve code understanding without truncating context.

### [Code Review Graph](tools/code-review-graph/meta.yaml)

![Phase 1](https://img.shields.io/badge/phase-1-brightgreen)
![Token reduction](https://img.shields.io/badge/token%20reduction-49x-brightgreen)
![Default ON](https://img.shields.io/badge/default-ON-brightgreen)
![Fork](https://img.shields.io/badge/fork-upstream--code--review--graph-blue)

Tree-sitter AST → local knowledge graph → MCP server.
Structural context replaces file dumps — **49× fewer tokens** on daily tasks.

- **Source:** https://github.com/tirth8205/code-review-graph
- **Install:** `uvx code-review-graph`
- **Keywords:** Tree-sitter, AST, knowledge graph, MCP, context optimization

---

## 🗄️ Vector Databases

Semantic search backends. Activated in **Phase 2** (multi-user or company tenant).

> [!WARNING]
> Vector databases are infrastructure tools.
> Install instructions are fetched from official docs at Phase 2 setup time.

### Comparison

| | [Qdrant](tools/qdrant/meta.yaml) | Chroma | Weaviate | Milvus |
|---|---|---|---|---|
| Hybrid search native | ✅ (v1.10+) | ❌ | ⚠️ partial | ✅ |
| JWT per collection | ✅ | ❌ | ✅ | ✅ |
| ARM64 support | ✅ | ✅ | ⚠️ | ⚠️ |
| Self-hosted | ✅ | ✅ | ✅ | ✅ |
| Suited for personal scale | ✅ | ✅ | ⚠️ heavier | ❌ overkill |
| **Recommended** | ✅ **Yes** | ❌ | ❌ | ❌ |

### [Qdrant](tools/qdrant/meta.yaml) ✅ Recommended

![Phase 2](https://img.shields.io/badge/phase-2-yellow)
![Hybrid search](https://img.shields.io/badge/hybrid%20search-native-brightgreen)
![ARM64](https://img.shields.io/badge/ARM64-supported-brightgreen)
![Company](https://img.shields.io/badge/maintained%20by-qdrant.tech-blue)

- **Docs:** https://qdrant.tech/documentation/
- **Install:** `docker run -p 6333:6333 -v qdrant-storage:/qdrant/storage qdrant/qdrant`

---

## 📄 Document Ingestion

Parse external documents into chunks for vector indexing. Phase 2, Block G4 option 3.

### Comparison

| | [Docling](tools/docling/meta.yaml) | Unstructured | MarkItDown | Apache Tika |
|---|---|---|---|---|
| PDF layout-aware | ✅ | ✅ | ⚠️ basic | ✅ |
| Local processing default | ✅ | ❌ cloud | ✅ | ✅ |
| ARM64 | ✅ | ⚠️ | ✅ | ⚠️ Java |
| Structured output | ✅ JSON/MD | ✅ | ✅ MD only | ✅ XML |
| **Recommended** | ✅ **Yes** | ❌ | ⚠️ simple tasks | ❌ |

### [Docling](tools/docling/meta.yaml) ✅ Recommended

![Phase 2](https://img.shields.io/badge/phase-2-yellow)
![Local](https://img.shields.io/badge/processing-local-brightgreen)
![Company](https://img.shields.io/badge/maintained%20by-IBM%20Research-blue)

- **Docs:** https://ds4sd.github.io/docling/
- **Install:** `pip install docling`

---

## 🔢 Embedding Models

Local models for vector indexing. Phase 2+ — activated when Qdrant is set up.

> [!NOTE]
> Embedding models run locally on your hardware.
> RAM requirements and quality trade-offs documented per entry.

### [BGE-M3](tools/bge-m3/meta.yaml) — Phase 2 upgrade path

![Phase 2](https://img.shields.io/badge/phase-2-yellow)
![Local](https://img.shields.io/badge/inference-local-brightgreen)
![Multilingual](https://img.shields.io/badge/languages-100%2B-blue)
![License](https://img.shields.io/badge/license-MIT-green)

Unified embedding model: dense + sparse (BM25-like) + ColBERT in one pass.
Replaces `nomic-embed-text` + separate BM42 index. Polish language supported.

- **Source:** https://github.com/FlagOpen/FlagEmbedding
- **HuggingFace:** https://huggingface.co/BAAI/bge-m3
- **Install:** `pip install -U FlagEmbedding`
- **RAM:** ~2 GB (FP16)
- **Phase 1 default:** use `nomic-embed-text` (lighter). Migrate here for quality.

---

## Adding a tool

See [CONTRIBUTING.md](CONTRIBUTING.md) for the entry format.

New tools are proposed quarterly and reviewed before being added.
The `categories.yaml` per tool is written after analysing repo contents.

> [!NOTE]
> `README.md` is regenerated after each quarterly review run.
> Do not edit it manually — edit `tools/<id>/meta.yaml` or `categories/_index.yaml` instead.
