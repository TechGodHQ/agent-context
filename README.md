# agent-context

Centralized engineering context for TechGodHQ repositories and the canonical
organization layer for Creed's layered-source design.

## Contents

- `.creed/config/org.md` — the compact, always-loaded TechGodHQ engineering
  constitution and repository policy.
- `.creed/skills/architecture.md` — repository boundaries, capability
  placement, contracts, dependencies, and Hydra surface projection.
- `.creed/skills/implementation.md` — LLM-native implementation rules and the
  required integration and agent-acceptance evidence.
- `.creed/skills/review.md` — organization-wide pull request review process and
  blocking findings.

The generated `AGENTS.md` renders the constitution and all three procedure
skills inline as config entries, so generic AGENTS consumers reach every
central procedure without pointer files or duplicated source.

Consuming repositories keep repository-specific context in their local
`.creed/` directory. Organization-wide context remains centralized here.

## Consumption Status

Creed's layered local-plus-Git sources shipped in `afe5dbb` (post-v0.3.0
main; see COD-407). Consumers pin this repository as a git layer — for
example `remote: https://github.com/TechGodHQ/agent-context.git` with a
pinned commit `ref:` — and Creed composes it with the repository-local
`.creed/` layer. The installed v0.3.0 binary rejects layered manifests;
build Creed from main until a layered-capable release ships.
