# Definition of Done (VibeCoding Squad)

Project-wide completion bar. Complements per-task acceptance criteria.

A change is **Done** only when ALL applicable items pass.

## Code & Tests

- [ ] Implements approved spec/task acceptance criteria
- [ ] Unit tests for new/changed logic (or documented why exempt)
- [ ] Integration/e2e tests for user-facing flows when applicable
- [ ] All tests pass locally and in CI
- [ ] No new linter errors introduced
- [ ] Build succeeds

## Review & Quality

- [ ] Tech Lead review: no open Blockers
- [ ] Change linked to spec section or task ID
- [ ] No secrets, tokens, or PII in code or logs
- [ ] Dependencies added only with justification (SA/PO aware)

## Documentation

- [ ] Public APIs or contracts updated in docs
- [ ] ADR written for non-trivial architectural decisions
- [ ] README or runbook updated if setup/deploy changed
- [ ] Comments only where intent is non-obvious

## CI/CD

- [ ] Pipeline green on merge target branch
- [ ] Required checks not disabled or skipped
- [ ] Artifact version traceable to commit SHA

## Deploy & Operate

- [ ] Deployed to staging (or prod per plan) with runbook
- [ ] Smoke test passed in target environment
- [ ] Rollback steps documented and validated
- [ ] Logs and metrics exist for new code paths
- [ ] Alerts configured for user-visible failure modes

## Product

- [ ] PO acceptance criteria verified in staging/prod
- [ ] Known limitations documented (not hidden)
- [ ] Feature flags or kill switches for risky launches

## GSD Card Closed

- [ ] `done_definition` from phase card is met
- [ ] `risks / blockers` empty or explicitly accepted
- [ ] Handoff to next phase completed or marked N/A

## Exemptions

Document exemptions in the PR/commit message:

```text
DOD EXEMPT: [item] — reason: [...] — approved by: [role]
```

Never exempt: secrets hygiene, rollback for prod, tests on behavior changes.