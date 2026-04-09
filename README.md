# personal-ai-tools-registry

> [!NOTE]
> This is a **curated registry**, not a generic awesome-list.
> Every entry is evaluated for use in [Personal AI](https://github.com/DaceJoy/personal-ai-core-public) deployments:
> local-first · multi-tenant · privacy-aware · ARM64-compatible.

![Tools](https://img.shields.io/badge/tools-9-blue)
![Categories](https://img.shields.io/badge/categories-13-green)
![Maintained](https://img.shields.io/badge/maintained%20by-ecosystem--scout-orange)

---

## Contents

- [How to read this registry](#how-to-read-this-registry)
- [🏗️ Agent Frameworks & Architecture](#-agent-frameworks--architecture)
- [🧰 Skill Packs](#-skill-packs)
- [🔒 Security Scanning](#-security-scanning)
- [⚡ Code Context & Token Optimization](#-code-context--token-optimization)
- [🗄️ Vector Databases](#️-vector-databases)
- [📄 Document Ingestion](#-document-ingestion)
- [Adding a tool](#adding-a-tool)

---

## How to read this registry

Each tool lives in `tools/<tool-id>/` with two files:

| File | Purpose |
|------|---------|
| `meta.yaml` | Source URLs, install hints, relevance to PersonalAI, phase |
| `categories.yaml` | Detected categories, keywords, use cases (written by ecosystem-scout) |

**Phase** indicates when a tool becomes relevant:

| Phase | Trigger |
|-------|---------|
| ![Phase 1](https://img.shields.io/badge/phase-1%20now-brightgreen) | Single user, active now |
| ![Phase 2](https://img.shields.io/badge/phase-2%20multi--user-yellow) | Second user or company tenant added |
| ![Phase 3](https://img.shields.io/badge/phase-3%20scale-red) | Hundreds of users, enterprise |

> [!TIP]
> `upstream_fork` entries are forks maintained at `github.com/DaceJoy/upstream-<name>`.
> Fork sync is automated monthly by `capability-auditor`.

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

### [gstack](tools/gstack/meta.yaml)

![Phase 1](https://img.shields.io/badge/phase-1-brightgreen)
![Stars](https://img.shields.io/github/stars/garrytan/gstack?style=flat)
![Fork](https://img.shields.io/badge/fork-upstream--gstack-blue)

23 specialist roles by Garry Tan (YC CEO): CEO · Designer · QA · Security · Release Engineer.
Pattern: activate a specialist role for focused, expert-level responses.

- **Source:** https://github.com/garrytan/gstack
- **Keywords:** specialist skills, virtual team, role-based prompting

---

## 🔒 Security Scanning

Tools for auditing agent configs, hooks, MCP servers, and detecting secrets or injection risks.

### [AgentShield](tools/agentshield/meta.yaml)

![Phase 1](https://img.shields.io/badge/phase-1-brightgreen)
![OWASP](https://img.shields.io/badge/OWASP-LLM01%20LLM02%20LLM06%20LLM07-red)
![Fork](https://img.shields.io/badge/fork-upstream--agentshield-blue)

102 security rules across 5 categories. Used as **verify-checklist step 14**
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
> Vector databases are infrastructure, not capability upstreams.
> They are not tracked in `sources.template.yaml` — install instructions
> are fetched from official docs at Phase 2 setup time.

### [Qdrant](tools/qdrant/meta.yaml) ✅ Recommended

![Phase 2](https://img.shields.io/badge/phase-2-yellow)
![Hybrid search](https://img.shields.io/badge/hybrid%20search-native-brightgreen)
![ARM64](https://img.shields.io/badge/ARM64-supported-brightgreen)
![Company](https://img.shields.io/badge/maintained%20by-qdrant.tech-blue)

Native hybrid search (dense + BM42 sparse) · JWT per collection · ARM64 binary.

- **Docs:** https://qdrant.tech/documentation/
- **Install:** `docker run -p 6333:6333 -v qdrant-storage:/qdrant/storage qdrant/qdrant`
- **Alternatives evaluated:** Chroma (no JWT isolation) · Weaviate (heavier) · Milvus (enterprise scale)

---

## 📄 Document Ingestion

Parse external documents into chunks for vector indexing. Activated in **Phase 2** (Block G4 option 3).

### [Docling](tools/docling/meta.yaml) ✅ Recommended

![Phase 2](https://img.shields.io/badge/phase-2-yellow)
![Local](https://img.shields.io/badge/processing-local-brightgreen)
![Company](https://img.shields.io/badge/maintained%20by-IBM%20Research-blue)

Layout-aware PDF/DOCX/HTML parsing · local processing · structured Markdown output.

- **Docs:** https://ds4sd.github.io/docling/
- **Install:** `pip install docling`
- **Alternatives evaluated:** Unstructured (cloud default) · MarkItDown (simpler) · Apache Tika (Java)

---

## Adding a tool

See [CONTRIBUTING.md](CONTRIBUTING.md) for the entry format.

New tools are proposed by `ecosystem-scout` (quarterly) and reviewed by `capability-auditor`.
The `categories.yaml` per tool is written by ecosystem-scout after analysing repo contents.

> [!NOTE]
> `README.md` is regenerated by ecosystem-scout after each quarterly run.
> Do not edit it manually — edit `tools/<id>/meta.yaml` or `categories/_index.yaml` instead.
