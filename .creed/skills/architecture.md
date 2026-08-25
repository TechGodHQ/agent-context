# Architecture Skill

Use when creating a TechGodHQ repository, adding a major capability, changing
repository boundaries or cross-repository dependencies, or introducing a CLI,
HTTP, MCP, or other public interface.

## Process

1. **State the responsibility.** Describe the repository's single coherent
   capability in one sentence. A change belongs here only when that sentence
   naturally owns it.
2. **Map composition.** Identify inputs, outputs, side effects, durable state,
   and upstream and downstream contracts. Outputs should be usable as inputs
   without scraping prose or reconstructing hidden state.
3. **Place the capability.** Reuse or extend the repository that already owns
   it. Create a focused repository when the capability has an independent
   lifecycle. Keep orchestration separate from domain behavior.
4. **Define the contract.** Prefer explicit typed contracts, structured errors,
   deterministic behavior, and versionable schemas. Keep domain logic
   independent of transport concerns.
5. **Project public surfaces through Hydra.** Domain repositories provide
   Hydra-compatible contracts. Hydra generates CLI, HTTP, and MCP adapters
   from those contracts. Generated adapters may be emitted into and
   compiled by another repository, but that repository does not independently
   design or hand-write the adapter.
6. **Close projection gaps at the source.** When Hydra cannot expose a required
   contract, improve Hydra before adding a bespoke transport adapter. Record a
   temporary legacy exception with its rationale and removal condition when an
   immediate migration is genuinely impossible.
7. **Check dependency direction.** Reject circular dependencies, shared modules
   that accumulate unrelated behavior, and integration that requires either
   repository to understand the other's internals.

## Completion Criteria

The design is ready only when a reviewer can identify:

- the repository's one responsibility;
- the owner of every capability and side effect;
- the stable contract between repositories;
- how each public surface is projected by Hydra;
- how another tool or agent can consume the result independently.
