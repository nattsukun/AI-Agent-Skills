# Lifecycle Gates

Do not advance phases until the exit criteria pass. If a gate fails, stay in phase and fix.

---

## Gate 0 → DEFINE (`/vibe-ideate`)

**Entry:** User has an idea, problem, or vague request.

**Exit criteria:**
- [ ] Problem statement in one sentence
- [ ] Target user identified
- [ ] Success metric named (even if approximate)
- [ ] PO approved MVP boundary (in / out)
- [ ] GSD card written with PO as owner

**Fail → stay:** "Build me an app" with no user or outcome.

---

## Gate 1 → SPEC (`/vibe-spec`)

**Entry:** DEFINE gate passed.

**Exit criteria:**
- [ ] PRD or spec file drafted (objective, users, flows)
- [ ] User stories with acceptance criteria
- [ ] Boundaries: Always / Ask first / Never
- [ ] Open questions listed (or explicitly "none")
- [ ] Human reviewed spec (or labeled ASSUMED for solo runs)
- [ ] GSD card with BA as owner

**Fail → stay:** No testable acceptance criteria.

---

## Gate 2 → PLAN (`/vibe-plan`)

**Entry:** SPEC gate passed.

**Exit criteria:**
- [ ] Task DAG with dependencies
- [ ] Each task: acceptance + verify + files (~5 max)
- [ ] SA architecture note or ADR for non-trivial decisions
- [ ] Milestones with T-shirt estimates
- [ ] Risk register with mitigations
- [ ] GSD card with PM as owner

**Fail → stay:** Tasks are vague ("implement auth") without verify steps.

---

## Gate 3 → BUILD (`/vibe-build`)

**Entry:** PLAN gate passed (or explicit hotfix path with BA mini-spec).

**Exit criteria (per slice):**
- [ ] One task acceptance criteria met
- [ ] Tests added/updated for behavior change
- [ ] Build passes locally or in CI
- [ ] Atomic commit with message referencing task
- [ ] GSD card updated: do_now = next slice

**Fail → stay:** Slice spans multiple tasks or lacks tests.

---

## Gate 4 → VERIFY (`/vibe-test`)

**Entry:** BUILD slice complete.

**Exit criteria:**
- [ ] Test plan executed (not just written)
- [ ] Results attached (command output, screenshot, log)
- [ ] Bugs filed with severity or "none found"
- [ ] Acceptance criteria traced to test cases
- [ ] GSD card with QA as owner

**Fail → stay:** "Manual testing looks fine" with no evidence.

---

## Gate 5 → REVIEW (`/vibe-review`)

**Entry:** VERIFY gate passed for the change set.

**Exit criteria:**
- [ ] Tech Lead review completed
- [ ] No Blocker-severity items open
- [ ] Change size reasonable or split plan exists
- [ ] Security-sensitive paths flagged to SA if needed
- [ ] GSD card with Tech Lead merge decision

**Fail → stay:** Blockers open or missing spec/task link in PR.

---

## Gate 6 → SHIP (`/vibe-ship`)

**Entry:** REVIEW gate passed.

**Exit criteria:**
- [ ] CI/CD pipeline green on target branch
- [ ] Deploy runbook followed (or dry-run documented)
- [ ] Rollback steps documented and tested
- [ ] SRE: logs/metrics/alerts for new paths
- [ ] PO acceptance criteria re-checked in staging/prod
- [ ] GSD card: done_definition met, owner = DevOps

**Fail → stay:** Prod deploy without rollback or monitoring.

---

## Hotfix Fast Path

For production incidents only:

```
/vibe-build (minimal fix) → /vibe-test (regression) → /vibe-ship (with rollback ready)
```

Still require: repro steps, test evidence, post-incident spec update within 24h.

---

## Parallel Work Rules

| Can parallelize | Must sequence |
|-----------------|---------------|
| UX flows while SA drafts API | Spec before plan |
| QA writes test plan during build | Build before verify sign-off |
| SRE drafts alerts during build | Review before prod ship |
| CI/CD pipeline work during plan | Plan before multi-file build |