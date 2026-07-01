# Command Playbooks

Step-by-step instructions per slash command. Load `vibecoding-squad-gsd` skill first.

---

## /vibe-ideate

**Roles:** PO (lead), BA (support), UX (optional)

**Steps:**
1. State `SQUAD STATUS` block
2. Ask at most 3 clarifying questions (or use reasonable assumptions labeled)
3. Produce product brief:
   - Problem statement
   - Target user
   - Current vs desired state
   - Success metric
   - MVP in / out
4. Fill DEFINE GSD card (`references/gsd-card.md`)
5. Check Gate 0 (`references/lifecycle-gates.md`)
6. Handoff → BA for `/vibe-spec`

---

## /vibe-spec

**Roles:** BA (lead), PO (review), SA (advisory on technical boundaries)

**Steps:**
1. Load product brief from ideate (or ask user to paste)
2. Surface assumptions block
3. Write spec using template:

```markdown
# Spec: [Name]

## Objective
## Users & Jobs
## User Stories
## Acceptance Criteria (Given/When/Then)
## Flows (happy + error)
## Tech Stack (if known)
## Commands (build/test/lint/dev)
## Project Structure
## Testing Strategy
## Boundaries
- Always:
- Ask first:
- Never:
## Success Criteria
## Open Questions
```

4. PO reviews MVP alignment (note approval or ASSUMED)
5. Fill SPEC GSD card
6. Check Gate 1
7. Handoff → PM + SA for `/vibe-plan`

**Save to:** `docs/specs/[feature-name].md` or project convention

---

## /vibe-plan

**Roles:** PM (lead), SA (co-lead), BA (stories), Dev (feasibility)

**Steps:**
1. Load approved spec
2. SA produces architecture summary + ADRs if needed
3. PM decomposes into tasks:

```markdown
- [ ] T-001: [description]
  - Acceptance: [...]
  - Verify: [command or check]
  - Files: [...]
  - Depends: [T-000 | none]
  - Size: S|M|L
```

4. Order tasks by dependency (not importance)
5. Identify parallel tracks (UX, CI/CD prep)
6. Risk register (top 3)
7. Fill PLAN GSD card
8. Check Gate 2
9. Handoff → Dev for `/vibe-build` starting T-001

---

## /vibe-build

**Roles:** Dev (lead), SA (contracts), UX (UI tasks)

**Steps:**
1. Pick **one** task from plan (state task ID)
2. Load spec section + relevant source files only (context discipline)
3. Implement thinnest vertical slice
4. Write/update tests first or alongside (TDD preferred)
5. Run verify command from task
6. Atomic commit: `feat(T-001): description`
7. Fill BUILD GSD card for this slice
8. Check Gate 3
9. If more tasks → repeat; else handoff → QA `/vibe-test`

**`/vibe-build auto`:** After human approves plan once, loop steps 1–9 for all tasks. Pause on failure, blocker, or task exceeding 5 files.

---

## /vibe-test

**Roles:** QA (lead), Dev (fixes)

**Steps:**
1. Load spec acceptance criteria + completed task list
2. Write/confirm test plan (unit / integration / e2e / manual)
3. Execute tests — attach output
4. Map each acceptance criterion → test case → result
5. File bugs with repro steps (or "none")
6. Fill VERIFY GSD card
7. Check Gate 4
8. Handoff → Tech Lead `/vibe-review` or back to Dev if bugs

---

## /vibe-review

**Roles:** Tech Lead (lead), QA (acceptance), SA (security/architecture if needed)

**Five-axis review:**
1. Correctness — does it meet acceptance?
2. Design — fits architecture and patterns?
3. Tests — adequate and meaningful?
4. Security — input validation, auth, secrets?
5. Maintainability — readable, right-sized change?

**Severity labels:** Nit | Optional | FYI | Blocker

**Steps:**
1. Review diff against spec/task
2. Produce review summary
3. Decision: Approve | Request changes | Split PR
4. Fill REVIEW GSD card
5. Check Gate 5
6. Handoff → DevOps `/vibe-ship`

---

## /vibe-ship

**Roles:** DevOps (lead), CI/CD (pipeline), SRE (observability), QA (smoke)

**Steps:**
1. Confirm CI green on release branch
2. Run deploy runbook (staging first unless hotfix)
3. Execute smoke tests
4. Validate rollback procedure
5. SRE: confirm logs, metrics, alerts for new paths
6. PO re-check acceptance in deployed environment
7. Fill SHIP GSD card
8. Check Gate 6
9. Close with release notes + monitoring links

---

## Quick Routing (no command given)

| Signal | Route to |
|--------|----------|
| "I have an idea" | /vibe-ideate |
| "Write a spec/PRD" | /vibe-spec |
| "Break this down" | /vibe-plan |
| "Implement/build" | /vibe-build |
| "Test this" | /vibe-test |
| "Review my PR" | /vibe-review |
| "Deploy/release" | /vibe-ship |
| Production incident | Hotfix fast path in lifecycle-gates.md |