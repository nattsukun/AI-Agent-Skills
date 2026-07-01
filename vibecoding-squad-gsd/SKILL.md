---
name: vibecoding-squad-gsd
description: >
  Enixera VibeCoding Squad — production-grade agent workflow with clear team roles
  (PO, PM, BA, SA, UX, Dev, Tech Lead, QA, DevOps, CI/CD, SRE) and GSD execution cards.
  Use when building software with AI agents, running /vibe-spec /vibe-plan /vibe-build /vibe-test
  /vibe-review /vibe-ship, orchestrating a full squad, or turning vague ideas into shipped code.
  Triggers: vibecoding squad, vibe squad, GSD team, agent team workflow, Enixera delivery.
metadata:
  author: Nattsu
  organization: Boo AI BootCamp
  credit: Nattsu | Boo AI BootCamp
---

# VibeCoding Squad GSD

**Credit:** Nattsu | Boo AI BootCamp

Enixera's own delivery system: **agent-skills lifecycle** + **GSD execution cards** + **named squad roles**.

Inspired by [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills). Adapted for VibeCoding — spec before code, thin slices, proof before ship, no motivational fluff.

## Lifecycle

```
  DEFINE          PLAN           BUILD          VERIFY         REVIEW          SHIP
 ┌──────┐      ┌──────┐      ┌──────┐      ┌──────┐      ┌──────┐      ┌──────┐
 │ Idea │ ───▶ │ Plan │ ───▶ │ Code │ ───▶ │ Test │ ───▶ │ Gate │ ───▶ │ Live │
 │Value │      │ Arch │      │ Slice│      │Proof │      │Review│      │ Ship │
 └──────┘      └──────┘      └──────┘      └──────┘      └──────┘      └──────┘
 /vibe-ideate   /vibe-spec    /vibe-build    /vibe-test    /vibe-review   /vibe-ship
                /vibe-plan
```

## Squad Roster (who owns what)

| Role | Phase | Owns | Delivers |
|------|-------|------|----------|
| **PO** (Product Owner) | DEFINE | Vision, priority, value, scope cuts | Product brief, MVP boundary, success metrics |
| **BA** (Business Analyst) | DEFINE | Requirements, stories, acceptance criteria | PRD sections, user stories, edge cases |
| **PM** (Project Manager) | PLAN | Timeline, dependencies, risks, milestones | Sprint plan, task DAG, blocker log |
| **SA** (Solution Architect) | PLAN / BUILD | Architecture, contracts, tech decisions | Architecture doc, ADRs, interface contracts |
| **UX** (UX/UI Designer) | BUILD | Flows, layout, accessibility | Wireframe notes, component spec, a11y checklist |
| **Dev** (Developer) | BUILD | Implementation, tests, commits | Working slices, unit tests, commit messages |
| **Tech Lead** | REVIEW | Code health, patterns, change size | Review notes, refactor list, merge decision |
| **QA** | VERIFY / REVIEW | Test strategy, regression, acceptance | Test plan, test results, bug report |
| **DevOps** | SHIP | Infra, env, deploy, rollback | Runbook, env config, deploy steps |
| **CI/CD** | SHIP | Pipelines, gates, artifacts | Pipeline config, gate checklist |
| **SRE** | SHIP | Logs, metrics, alerts, cost | Observability plan, alert rules |

Read full role playbooks: `references/squad-roster.md`

## Command Router

When the user invokes a slash command or describes work, route to the right phase and squad:

| User intent | Command | Lead roles | Supporting roles |
|-------------|---------|------------|------------------|
| Rough idea, unclear ask | `/vibe-ideate` | PO, BA | UX |
| Write spec / PRD | `/vibe-spec` | BA, PO | SA |
| Break into tasks + architecture | `/vibe-plan` | PM, SA | BA, Dev |
| Implement one slice | `/vibe-build` | Dev | SA, UX |
| Prove it works | `/vibe-test` | QA | Dev |
| Quality gate before merge | `/vibe-review` | Tech Lead, QA | SA |
| Deploy + monitor | `/vibe-ship` | DevOps, CI/CD | SRE, QA |

**`/vibe-build auto`** — After an approved plan, implement every task autonomously. Still one slice at a time, still verify each slice, still pause on failure or risky steps.

## Core Workflow (every engagement)

### 1. Discover phase

Identify lifecycle phase. If unclear, start with `/vibe-ideate` (PO + BA interview).

### 2. Assign squad lead

One role leads output; others review. State it explicitly:

```
SQUAD ACTIVE: PO + BA (DEFINE)
LEAD: BA
SUPPORT: PO, SA (advisory)
```

### 3. Produce a GSD Card

Every phase ends with a GSD card. Template: `references/gsd-card.md`

```text
Goal:
Scope:
Do now:
Do next:
Done definition:
Risks / blockers:
Assumptions:
Owner:
```

### 4. Gate before advancing

Do not move to the next phase until the current gate passes. Gates: `references/lifecycle-gates.md`

### 5. Handoff packet

When passing to the next phase, deliver a handoff block:

```text
HANDOFF: [FROM ROLE] → [TO ROLE]
Artifact: [file or section]
Decisions locked: [...]
Open questions: [...]
Next GSD do_now: [...]
```

## Operating Rules (non-negotiable)

These apply across all roles. Full detail: `references/operating-rules.md`

1. **Surface assumptions** before non-trivial work.
2. **Stop on confusion** — name the conflict, ask, wait.
3. **Push back** when an approach has clear downsides.
4. **Enforce simplicity** — boring beats clever.
5. **Scope discipline** — touch only what the task requires.
6. **Verify, don't assume** — evidence required; see `references/definition-of-done.md`.

## Full Feature Sequence

Typical order for a non-trivial feature:

```
1.  /vibe-ideate     PO + BA     → product brief + problem statement
2.  /vibe-spec       BA + PO     → PRD with acceptance criteria
3.  /vibe-plan       PM + SA     → task DAG + architecture + milestones
4.  /vibe-build      Dev         → vertical slices (repeat per task)
5.  /vibe-test       QA          → test plan + execution per slice
6.  /vibe-review     Tech Lead   → code review gate
7.  /vibe-ship       DevOps      → deploy + CI/CD + SRE observability
```

Not every task needs every step. A bug fix: `/vibe-build` → `/vibe-test` → `/vibe-review`.

## Output Format (default response)

When executing this skill, structure replies as:

### Squad Status
- Phase, active roles, lead role, current task

### Artifact
- The deliverable for this phase (brief, spec section, plan, code, test report, etc.)

### GSD Card
- Filled card for this phase

### Handoff
- Who receives work next and what they need

### Verification
- What was checked and evidence (test output, build, manual step)

## References

| File | Use when |
|------|----------|
| `references/squad-roster.md` | Role responsibilities, deliverables, anti-patterns |
| `references/lifecycle-gates.md` | Phase exit criteria |
| `references/gsd-card.md` | Card templates per phase |
| `references/operating-rules.md` | Shared agent behaviors |
| `references/definition-of-done.md` | Project-wide completion bar |
| `references/command-playbooks.md` | Step-by-step per slash command |
| `commands/*.md` | Copy-paste slash command entry points |

## Quality Bar

Before finishing any phase:

- [ ] Lead role deliverable exists and is concrete
- [ ] GSD card has `do_now`, `done_definition`, and `owner`
- [ ] Assumptions are labeled, not hidden
- [ ] Gate criteria for this phase are met
- [ ] Handoff names the next role and artifact path
- [ ] Verification evidence is attached (not "looks good")

## Relationship to Other Enixera Skills

- `vibecoding-gsd-framework` — lightweight GSD cards for any task (content, marketing, ops). Use for non-software work.
- `vibecoding-squad-gsd` (this skill) — full software squad lifecycle with roles and gates.
- `vibecoding-book-creator` — book production; can invoke squad for chapter tooling features.

---

*VibeCoding Squad GSD — Nattsu | Boo AI BootCamp · Enixera*