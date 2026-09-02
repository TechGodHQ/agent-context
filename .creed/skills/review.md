# Org Review Skill

Use when reviewing any TechGodHQ pull request.

## Review Process

1. Read the issue, specification, and repository responsibility before reading
   the diff. Confirm the change satisfies the goal and belongs in this
   repository.
2. Check architectural boundaries. Reject duplicated capabilities, unrelated
   orchestration, circular dependencies, hidden cross-repository knowledge,
   and side effects owned by the wrong component.
3. Check public surfaces. Domain repositories define typed contracts; Hydra
   projects CLI, HTTP, and MCP adapters. Generated adapters may
   reside in another repository, but independently designed or hand-written
   transport adapters require a documented legacy exception.
4. Check LLM-native operation. An unfamiliar agent should be able to discover
   the interface, supply structured input, run it non-interactively, interpret
   structured output and errors, and compose the result without an LLM being a
   runtime requirement.
5. Run the repository's complete gate commands from `AGENTS.md`.
6. Inspect verification evidence. Where feasible, require deterministic
   integration coverage at the nearest real public boundary and the exact
   commands and observed result from an agent acceptance pass. When either is
   infeasible, require the reason and the strongest reproducible fallback.
   Unit-only evidence is insufficient for externally observable behavior when
   integration coverage is feasible.
7. Verify at least one producer-consumer path or versioned boundary fixture
   when a cross-repository contract changes.
8. Check generated and synchronized output for determinism and drift when the
   diff touches code generation, Hydra projection, or Creed-managed files.
9. Look for regressions in public contracts, schemas, structured errors,
   idempotency, retry behavior, output composition, and explicit side effects.

## Blocking Findings

Block approval when the change:

- weakens the repository's single responsibility for implementation
  convenience;
- introduces a hand-written surface Hydra should project;
- requires an LLM for deterministic core behavior;
- omits feasible integration or agent-acceptance evidence, or omits the
  infeasibility rationale and strongest reproducible fallback;
- cannot be operated from committed repository guidance;
- leaves generated output or cross-repository compatibility unverified;
- couples core functionality to a specific provider. Providers are libraries,
  not routes: public operations are named for the noun (e.g. `ingest_batch`), a
  provider name must never appear in generated-operation names, HTTP paths,
  core crates, or hardcoded source-string checks outside the provider crate
  itself. New providers are added by depending on the provider crate plus one
  config entry — if adding a provider would touch core/server/cli/mcp surfaces,
  block and redesign.

## Review Bias

Prefer correctness, product behavior, composability, and reproducible evidence
over style nits. Raise style comments only when they prevent future bugs or
contract confusion.
