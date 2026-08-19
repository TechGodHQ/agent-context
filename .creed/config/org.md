# TechGodHQ Org Context

TechGodHQ builds modular, LLM-native peer tools: explicit definitions over
inference, committed generated code, boring implementations. Repos: hydra
(shared projection layer), iris (unified messaging), rite, coldmic, creed
(this context's consumer).

## Public + MIT, always

All TechGodHQ repositories are public and MIT-licensed. Never create private
repos. Never commit secrets.

## Commit & PR Rules

- Shiv's global git identity signs everything.
- Conventional commits: `feat:`, `fix:`, `refactor:`, `docs:`, `chore:`.
- PRs may carry `Co-authored-by: Archon <archon@purelymail.com>` for
  runner-generated work. Never add "Generated with ..." tool footers.
- Auto-merge is permitted per the standing gate policy: CI green and gate
  confidence >= 0.80.
- PR discipline on protected repos: changes land through PRs, not direct
  pushes to main.

