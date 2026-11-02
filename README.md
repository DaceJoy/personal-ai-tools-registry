# personal-ai-tools-registry

> [!NOTE]
> This is a **curated registry**, not a generic awesome-list.
> Every entry is evaluated for use in [Personal AI](https://github.com/DaceJoy/personal-ai-core-public) deployments:
> local-first · multi-tenant · privacy-aware · ARM64-compatible.

![Tools](https://img.shields.io/badge/tools-45-blue)
![Categories](https://img.shields.io/badge/categories-28-green)
![Maintained](https://img.shields.io/badge/maintained%20by-manual%20%2B%20upstream--movement%20feed-orange)

---

> Special thanks to **[Daniel Miessler](https://github.com/danielmiessler)** for the inspiration.
> This registry exists because of his work on [Personal AI Infrastructure](https://github.com/danielmiessler/LifeOS).

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

> [!WARNING]
> `upstream_fork` entries point to forks kept as **deletion insurance only**. Fork sync is
> NOT automated and never was: measured 2026-11-01, all 5 forks had been pushed exactly once
> each at creation (2026-04-08/16) and were 207-209 days stale, while this file claimed
> "automated monthly" -- which is precisely why nobody checked. How far behind each fork is
> now runs weekly (`upstream_ahead_of_fork` in the feed below) and surfaces as a signal, but
> **bringing a fork forward is still a human action**.
>
> | | our fork | upstream branch | commits behind, 2026-11-01 |
> |---|---|---|---|
> | pai | `DaceJoy/upstream-pai` | `main` | **124** |
> | code-review-graph | `DaceJoy/upstream-code-review-graph` | `staging` | **1077** |
> | agentshield | `DaceJoy/upstream-agentshield` | `main` | **96** |
> | everything-claude-code | `DaceJoy/upstream-everything-claude-code` | `main` | **3115** |
> | gstack | `DaceJoy/upstream-gstack` | `main` | **569** |
>
> The branch column matters: our `upstream-code-review-graph` fork tracks `main` while its
> upstream develops on `staging`, so the count is measured against the branch upstream actually
> moves, not the one the fork happens to default to.

---

## Review status

> [!NOTE]
> `last_verified` and the `upstream_head` PIN live in each `tools/<id>/meta.yaml`; this table
> mirrors them. Entries not reviewed in **90+ days** are due for re-verification -- a human
> pass, not an agent. What is automated is NOTICING: `upstream-movement-feed.py` compares each
> entry's pin against its upstream's live head every week and raises a signal when they differ.
> Nothing flagged these entries between 2026-04-09 and 2026-11-01 (206 days) because the
> flagger was a sentence in a document rather than a program.

| Tool | Last verified | Pin (`upstream_head`) | Phase | Status |
|------|--------------|----------------------|-------|--------|
| [PAI](tools/pai/meta.yaml) | 2026-11-01 | `b7efec97` | 1 | ✅ active |
| [everything-claude-code](tools/everything-claude-code/meta.yaml) | 2026-11-01 | `b38be6a7` | 1 | ✅ active |
| [agentshield](tools/agentshield/meta.yaml) | 2026-11-01 | `b0891303` | 1 | ✅ active |
| [code-review-graph](tools/code-review-graph/meta.yaml) | 2026-11-01 | `d72e8fbf` | 1 | ✅ active |
| [gstack](tools/gstack/meta.yaml) | 2026-11-01 | `f7397563` | 1 | ✅ active |
| [qdrant](tools/qdrant/meta.yaml) | 2026-11-01 | `222b2e44` | 2 | ✅ active |
| [docling](tools/docling/meta.yaml) | 2026-11-01 | `26a5bcfd` | 2 | ✅ active |
| [bge-m3](tools/bge-m3/meta.yaml) | 2026-11-01 | `897baa67` | 2 | 👀 watch |
| [mcp-obsidian](tools/mcp-obsidian/meta.yaml) | 2026-11-01 | `5ee0b84f` | 2 | 👀 watch |
| [splade](tools/splade/meta.yaml) | 2026-11-01 | `8dcd33a0` | 2 | 👀 watch |
| [polish-splade](tools/polish-splade/meta.yaml) | 2026-11-01 | `13649a1c` | 2 | 👀 watch |
| [agent-browser (Vercel Labs)](tools/agent-browser/meta.yaml) | 2026-11-01 | `5868f7c05020` | 3 | 👀 watch |
| [Agent-Reach](tools/agent-reach/meta.yaml) | 2026-11-01 | `7a38047acf26` | 1 | 👀 watch |
| [AstraQuant (patterns only, OWNED-ELSEWHERE)](tools/astra-quant-agent/meta.yaml) | 2026-11-01 | `e0b29fef1818` | 1 | 👀 watch |
| [Awesome Free LLM APIs](tools/awesome-free-llm-apis/meta.yaml) | 2026-11-01 | `2527fd445fb9` | 1 | 👀 watch |
| [Caveman](tools/caveman/meta.yaml) | 2026-11-01 | `9b68f7ed12b0` | 1 | 👀 watch |
| [ChatGPT YouTube Agent Skill](tools/chatgpt-youtube-agent-skill/meta.yaml) | 2026-11-01 | `6314d3c17dfa` | 2 | 👀 watch |
| [Chrome DevTools MCP](tools/chrome-devtools-mcp/meta.yaml) | 2026-11-01 | `8d009e854f8a` | 2 | 👀 watch |
| [Claude Code Usage Monitor](tools/claude-code-usage-monitor/meta.yaml) | 2026-11-01 | `c59a83bf943f` | 1 | 👀 watch |
| [Claude Code Usage Dashboard (phuryn)](tools/claude-usage-phuryn/meta.yaml) | 2026-11-01 | `3eea154474e9` | 2 | 👀 watch |
| [Context7](tools/context7/meta.yaml) | 2026-11-01 | `7836c5839183` | 2 | 👀 watch |
| [Crawl4AI](tools/crawl4ai/meta.yaml) | 2026-11-02 | `888299fb5f0b` | 1 | ✅ active |
| [DiscordChatExporter](tools/discordchatexporter/meta.yaml) | 2026-11-01 | `14ee1f64906c` | 1 | ✅ active |
| [House Planner](tools/house-planner/meta.yaml) | 2026-11-01 | `5c91280da6c5` | 3 | 👀 watch |
| [Hypit](tools/hypit/meta.yaml) | 2026-11-01 | `0762c6be56c0` | 2 | 👀 watch |
| [kimi-k3-in-c](tools/kimi-k3-in-c/meta.yaml) | 2026-11-01 | `81bb6c23ccee` | 3 | 👀 watch |
| [Logo Design Skill](tools/logo-design-skill/meta.yaml) | 2026-11-01 | `734090317a21` | 3 | 👀 watch |
| [LongCat-DeepResearch](tools/longcat-deepresearch/meta.yaml) | 2026-11-01 | `f8d3a99dabba` | 2 | 👀 watch |
| [MiroFish](tools/mirofish/meta.yaml) | 2026-11-01 | `7657031ac011` | 2 | 👀 watch |
| [NextChat](tools/nextchat/meta.yaml) | 2026-11-01 | `1d3dc3315129` | 3 | 👀 watch |
| [Obscura](tools/obscura/meta.yaml) | 2026-11-01 | `8534b401898e` | 2 | 👀 watch |
| [OpenCut](tools/opencut/meta.yaml) | 2026-11-01 | `e66801077856` | 3 | 👀 watch |
| [Orkas](tools/orkas/meta.yaml) | 2026-11-01 | `12f59a2e077b` | 3 | 👀 watch |
| [Papermorph](tools/papermorph/meta.yaml) | 2026-11-01 | `810e9bca280b` | 1 | 👀 watch |
| [Postiz](tools/postiz-app/meta.yaml) | 2026-11-01 | `4d13c6a2a847` | 3 | 👀 watch |
| [Replica Skill](tools/replica-skill/meta.yaml) | 2026-11-01 | `77c9436fb3d1` | 2 | 👀 watch |
| [Roast Room](tools/roast-room/meta.yaml) | 2026-11-01 | `e40f40652d56` | 2 | 👀 watch |
| [RTK (Rust Token Killer)](tools/rtk/meta.yaml) | 2026-11-01 | `16d1ccfd40d1` | 1 | 👀 watch |
| [Thinking Orbs](tools/thinking-orbs/meta.yaml) | 2026-11-01 | `de85557ca220` | 2 | 👀 watch |
| [skills (Vercel Labs CLI)](tools/vercel-skills-cli/meta.yaml) | 2026-11-01 | `92a9a34ac3bf` | 1 | 👀 watch |
| [web-scraper (yfe404)](tools/web-scraper/meta.yaml) | 2026-11-01 | `40ef9f8c45d4` | 1 | 👀 watch |
| [YominPost](tools/yominpost/meta.yaml) | 2026-11-01 | `12d7a35ea5ed` | 3 | 👀 watch |
| [YouTube Agent Skill (Jakeschincariol)](tools/youtube-agent-skill/meta.yaml) | 2026-11-01 | `a2feb2104981` | 2 | 👀 watch |
| [meituan-longcat CLASS W (12 weights)](tools/longcat-weights-class/meta.yaml) | 2026-11-01 | `1ac91dad53bc` | 3 | 👀 watch |
| [meituan-longcat CLASS B (12 benchmarks)](tools/longcat-benchmarks-class/meta.yaml) | 2026-11-01 | `edc4e80e642b` | 3 | 👀 watch |

> The 11 rows from PAI through `polish-splade` are the pre-existing entries (verified 2026-11-01
> by the S1b session of `FamilyPAI/MEMORY/WORK/20261030-230237_github-target-grill-and-source-
> repo-register`). The 33 rows below `polish-splade` were ADDED by that same thread's S9
> synthesis session (2026-11-01), one per non-REJECT verdict across its 37-target grill program
> (37 total minus 4 REJECT). Two of the 33 (`longcat-weights-class`, `longcat-benchmarks-class`)
> cover 12 repos each, graded together as one class rather than per-repo -- see that thread's
> `FIT-MATRIX.md` for the full needs x elements mapping. Every `upstream_head` pin
> above was read live via `gh api .../commits` at write time, not estimated.

> A re-verification pass, concretely (what the 2026-11-01 pass did): for each entry read
> `source.github`, confirm the repo resolves and is not archived, read its **default branch**
> (`code-review-graph` is `staging`, not `main`), record that branch's head SHA and date as
> `upstream_head` / `upstream_head_date`, set `last_verified`, and mirror both into the table
> above. An entry with no GitHub source is verified at its real source -- `polish-splade` at
> `huggingface.co/api/models/sdadas/polish-splade`, whose `sha` is its pin.

---

## 🏗️ Agent Frameworks & Architecture

Tools that provide conceptual foundations, architecture patterns, or orchestration models.

### [Personal AI Infrastructure (PAI)](tools/pai/meta.yaml)

![Phase 1](https://img.shields.io/badge/phase-1-brightgreen)
![Adoption](https://img.shields.io/badge/adoption-audit--only-lightgrey)
![Fork](https://img.shields.io/badge/fork-upstream--pai-blue)

Foundation architecture by Daniel Miessler. Conceptual base for this project's
multi-tenant extensions, capability auditor, and interview-driven setup.

- **Source:** https://github.com/danielmiessler/LifeOS
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

## 🔌 MCP Servers — Knowledge Access

MCP servers that give Claude Code live access to external knowledge sources.

### [mcp-obsidian](tools/mcp-obsidian/meta.yaml) — Phase 2, opt-in

![Phase 2](https://img.shields.io/badge/phase-2-yellow)
![Requires plugin](https://img.shields.io/badge/requires-Obsidian%20REST%20API%20plugin-orange)
![License](https://img.shields.io/badge/license-MIT-green)

Live search and read/write access to an Obsidian vault via MCP.
**Phase 1 alternative:** Zumi reads `.md` files directly — no plugin required.

- **Source:** https://github.com/MarkusPfundstein/mcp-obsidian
- **Install:** `uvx mcp-obsidian`
- **Requires:** Obsidian running + Local REST API community plugin
- **Operations:** list, browse, get content, search, insert, append, delete

---

## Adding a tool

See [CONTRIBUTING.md](CONTRIBUTING.md) for the entry format.

New tools are proposed quarterly and reviewed before being added.
The `categories.yaml` per tool is written after analysing repo contents.

> [!NOTE]
> There is NO generator for this file -- no script in this repo reads `meta.yaml` and writes
> `README.md`. The sentence that used to stand here ("regenerated after each quarterly review
> run, do not edit it manually") described one that was never written, so the table below drifted
> from the metas unnoticed. Until a generator exists, edit `tools/<id>/meta.yaml` **and** this
> file in the same commit, and treat any disagreement between them as a defect in this file.
