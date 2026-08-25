# Implementation Skill

Use when implementing or changing production behavior in a TechGodHQ
repository, including internal behavior whose correctness needs integration
evidence.

## Implementation Rules

- Use Rust when creating a new production repository. When another language is
  required, document the architectural constraint and expected lifetime of
  that repository-level exception.
- Keep the deterministic domain capability independent from any optional LLM
  workflow around it.
- Make interfaces self-describing where practical. Prefer typed schemas,
  structured inputs and outputs, stable error identifiers, and examples that
  can be executed as written.
- Keep normal operation non-interactive. Require explicit inputs rather than
  guessing intent, and make mutations and external side effects visible.
- Emit composable result data separately from diagnostics. Define partial
  failure, retry, and idempotency behavior where side effects are involved.
- Generate CLI, HTTP, and MCP adapters through Hydra from the same domain
  contract. Do not implement parallel transport semantics by hand.
- Keep generated artifacts deterministic and commit them when the repository's
  workflow requires committed generated output.

## Verification

1. Run the repository's complete gate commands from `AGENTS.md`.
2. Add deterministic integration coverage at the nearest real public boundary
   for every changed behavior where feasible. Unit tests remain useful for
   isolated edge cases but are not sufficient evidence by themselves.
3. Exercise the change as a consumer would, through the public contract or a
   Hydra-generated surface rather than an internal helper.
4. Where feasible, perform an agent acceptance pass: using only committed
   repository guidance, have an unfamiliar agent discover the interface,
   execute the changed behavior, and interpret the result. Record the exact
   commands and observed result in the pull request. When it is infeasible,
   record why and provide the strongest reproducible fallback evidence.
5. When a contract affects another repository, verify at least one real
   producer-consumer path or a versioned contract fixture shared at that
   boundary.

An LLM is not part of deterministic CI merely because an agent performs the
acceptance pass. CI proves repeatable behavior; the acceptance pass proves that
the intended agent user can discover and operate it.

## Completion Criteria

The change is done only when the gates pass, feasible integration and agent
acceptance evidence cover the behavior, generated output is stable, and the
pull request contains enough evidence for a reviewer to reproduce the result.
Any omitted evidence includes an infeasibility rationale and the strongest
available fallback.
