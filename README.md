# agent-context

Centralized agent context for TechGodHQ repositories, consumed via [creed](https://github.com/techgodhq/creed)'s git-remote source (`creed pull git@github.com:TechGodHQ/agent-context.git`).

## Contents

- `config/org.md` — org-wide rules: public+MIT, commit/PR conventions, gate policy.
- `skills/review.md` — org-wide PR review checklist.

Consuming repos keep repo-specific context local in `.creed/`; org-wide context is centralized here. See COD-407 for the v0.4 layered-source design this repo pilots.
