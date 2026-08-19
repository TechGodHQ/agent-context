# Org Review Skill

Use when reviewing any TechGodHQ pull request.

## Checklist

1. Read the issue or spec goal first. Do not review a diff in isolation.
2. Confirm the change actually satisfies the stated goal.
3. Run the repo's own gate commands from its AGENTS.md before approving.
4. Check generated/synced output determinism if the diff touches codegen
   or creed-managed files.
5. Look for user-visible regressions in CLI flags, output text, and public
   schemas.

## Review Bias

Prefer correctness and product behavior over style nits. Small style
comments are only worth raising if they prevent future bugs or API
confusion.
