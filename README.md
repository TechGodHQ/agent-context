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

The generated `AGENTS.md` contains explicit trigger-and-path pointers to these
skills so generic AGENTS consumers can load the source files when relevant.

Consuming repositories keep repository-specific context in their local
`.creed/` directory. Organization-wide context remains centralized here.

## Consumption Status

Layered local-plus-Git sources are tracked in COD-407 and are not available in
Creed v0.3.0. In that release, `creed pull` replaces the consumer's local
`.creed/` tree rather than merging this organization layer with repository
context. Do not use it as a layered install until COD-407 lands.
