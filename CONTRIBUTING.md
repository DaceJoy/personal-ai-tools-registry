# Contributing to personal-ai-tools-registry

## Adding a new tool

Create `tools/<tool-id>.yaml` using this template:

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

maintained_by: community | company | company-<name>
last_verified: <date>
added_by: ecosystem-scout | initial-setup | manual
added_reason: "<why this tool was added>"
```

## Adding a new category

Create `categories/<category-id>.yaml` following existing category files.
A category must have at least one `recommended: true` tool before being considered active.

## How entries are maintained

- `ecosystem-scout` proposes new entries quarterly → `capability-auditor` reviews → merged here
- `last_verified` updated when a tool is reviewed
- `status: deprecated` when a tool is no longer maintained or superseded
- Tools with `maintained_by: company` are not forked (low deletion risk)
- Tools with `maintained_by: community` should have a fork in the parent PersonalAI account
