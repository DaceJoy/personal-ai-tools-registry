# Contributing to personal-ai-tools-registry

## Adding a new tool

Create a DIRECTORY `tools/<tool-id>/` holding two files. A single flat YAML file per tool is NOT the
shape -- this document described that until 2026-11-01 while all 11 live entries used the
directory form, so the one document a contributor reads first was the one place that
disagreed with every entry in the repo.

### `tools/<tool-id>/meta.yaml`

```yaml
tool_id: <unique-id>
display_name: <Human Name>
category: <category-id>        # must match a file in categories/
status: active | watch | deprecated | experimental
type: infrastructure | skill-pack | agent-framework | security | embedding

source:
  github: <url or null>        # null if no official GitHub repo
  docs: <url>                  # REQUIRED — official documentation
  docker: <image or null>
  pypi: <package or null>

relevance_to_personalai:
  use_case: "<one sentence>"
  phase: 1 | 2 | 3
  replaces_what: <tool-id or null>
  alternatives: []

install:
  hint: "<quick install command>"
  docs_url: <url>
  arm64_support: true | false | unknown

maintained_by: community-<who> | company | company-<name>
                               # values in live use: community-individual,
                               # community-baai, company, company-ibm, company-naver
upstream_fork: <url or null>   # a fork we keep as deletion insurance; null = none needed
upstream_head: <sha or null>   # the commit this entry was last verified AGAINST (the PIN)
upstream_head_date: <date>     # that commit's date -- drift is measured from these two
last_verified: <date>
added_by: ecosystem-scout | initial-setup | manual
added_reason: "<why this tool was added>"
```

### `tools/<tool-id>/categories.yaml`

Detected categories, keywords and use cases for this tool. Written after reading the
upstream repo's contents, not guessed from its name. A third file, `comparison.yaml`
(side-by-side against alternatives), is optional -- no live entry has one yet.

## Adding a new category

Create `categories/<category-id>.yaml` following existing category files.
A category must have at least one `recommended: true` tool before being considered active.

## How entries are maintained

> [!WARNING]
> `ecosystem-scout` and `capability-auditor` are NOT IMPLEMENTED. They are named four times
> across this repo's docs and zero times in code -- no workflow, no cron, no script. Every
> entry below was written by hand at initial setup and nothing has reviewed them since.
> Measured 2026-11-01: all 11 entries sat at `last_verified: 2026-04-09` for 206 days, past
> this document's own 90-day flag, because the mechanism that was supposed to flag them was
> a sentence rather than a program. Treat the next two bullets as the intended design, not
> as a description of what runs.

- INTENDED: `ecosystem-scout` proposes new entries quarterly → `capability-auditor` reviews → merged here
- INTENDED: `last_verified` updated when a tool is reviewed

What ACTUALLY runs, as of 2026-11-01:

- `FamilyPAI/scripts/upstream-movement-feed.py`, weekly, appended to the existing lane-B cron
  line. It records every entry's upstream head SHA and date, compares them against the
  `upstream_head` pin in each `meta.yaml`, and measures how far behind each `upstream_fork` is.
  Actionable rows land in a snapshot feed read daily by `FamilyPAI/scripts/parked-trigger-watch.py`,
  which raises a YODO signal on transition. A re-verification pass is still a human session;
  what is automated is NOTICING that one is due.

> [!NOTE]
> DESIGN POINTER (not implemented): `FamilyPAI/MEMORY/WORK/20261030-230237_github-target-grill-
> and-source-repo-register/targets/T02-awesome-free-llm-apis.md` (HARVEST verdict, grilled
> 2026-11-01) found a sharper pattern than the feed above. `mnfst/awesome-free-llm-apis` runs a
> daily per-FACT probe (`agents/provider-sync.md`, `scripts/verify-providers.js`) that classifies
> each HTTP outcome as EVIDENCE or NOISE against a written table before editing any row, plus a
> separate `scripts/check-sources.js` pass that stores the exact quote used as proof of a prose
> claim (context window, pricing, feature list). `upstream-movement-feed.py` above answers "has
> the project moved"; it does not answer "is a specific claim inside a still-live entry still
> true" -- that is FamilyPAI's N04/N05/N15 (see that thread's `NEEDS.md`), still open. No code
> landed here for this note; it is a forward pointer, not a build.

- `status: deprecated` when a tool is no longer maintained or superseded. A fork of ours being
  stale is OUR failure, not upstream's, and is never grounds for deprecating an entry.
- Tools with `maintained_by: company*` are not forked (low deletion risk)
- Tools with `maintained_by: community*` should have a fork in the parent PersonalAI account.
  Creating that fork is not the end of the job: 5 forks were created 2026-04-08/16 and never
  pushed to again, while this README claimed "Fork sync is automated monthly". A fork protects
  against deletion; only the feed above protects against drift.
