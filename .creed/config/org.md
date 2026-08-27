# TechGodHQ Org Context

TechGodHQ builds small, composable tools that are native to LLM use without
requiring an LLM at runtime.

## Engineering Constitution

- **One capability per repository.** Keep repository responsibilities narrow,
  side effects explicit, and contracts composable. Prefer integrating focused
  tools over absorbing adjacent capabilities.
- **LLM-native, LLM-optional.** Interfaces must be discoverable, deterministic,
  non-interactive, and usable through structured inputs, outputs, and errors.
  Core behavior must remain useful without an LLM.
- **Rust by default.** Build new production repositories in Rust. Document the
  architectural reason for choosing another language.
- **One contract, projected surfaces.** Domain repositories define typed
  capabilities. Hydra is the canonical mechanism for projecting those
  contracts into CLI, HTTP, and MCP interfaces. Hydra-generated
  adapters may live in other repositories; outside a documented temporary
  legacy exception, independently designed or hand-written transport adapters
  may not.
- **Integration evidence defines done.** Unit tests support a change but do not
  prove it works. Exercise changed behavior through its real public boundary
  and treat difficulty using it as a product defect.

Before changing repository boundaries, dependencies, public contracts, or
transport surfaces, follow the Architecture Skill below. Before implementing
production behavior, follow the Implementation Skill below. Before reviewing
any pull request, follow the Org Review Skill below.

## Public + MIT, Always

All TechGodHQ repositories are public and MIT-licensed. Never create private
repositories or commit secrets.

## Commit and Pull Request Rules

- Shiv's global Git identity signs everything.
- Use conventional commits: `feat:`, `fix:`, `refactor:`, `docs:`, `chore:`.
- Runner-generated work may carry
  `Co-authored-by: Archon <archon@purelymail.com>`.
- Omit tool-generated attribution footers.
- Land changes through pull requests rather than direct pushes to `main`.
- Auto-merge is permitted when CI is green and gate confidence is at least
  0.80.

## Public Release Authority

- Published tags and releases are immutable. Never move, delete, or rewrite a
  published tag to repair release contents; publish a new, truthfully versioned
  correction instead.
- Agents may prepare correction-release changes, update version constants and
  release documentation, and run release verification without separate
  approval.
- Publishing a new public tag or release requires Shiv's authorization unless
  the linked ticket or its comments already explicitly authorize that exact
  release. Existing explicit authorization is sufficient and must not be
  requested twice.
- When authorization is absent, report an explicit `Blocked: release
  authorization` state naming the proposed version. Do not silently re-plan or
  leave the work parked without a labeled blocker.
- After authorization, verify the remote tag/release and a clean consumer
  installation or equivalent public-boundary check before declaring the release
  complete.
