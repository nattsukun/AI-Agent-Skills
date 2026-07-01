# GSD Card Templates

GSD = **Get Stuff Done**. Every VibeCoding squad phase ends with a filled card.

## Universal Template

```text
Goal:
Scope:
Do now:
Do next:
Done definition:
Risks / blockers:
Assumptions:
Owner: [PO|BA|PM|SA|UX|Dev|Tech Lead|QA|DevOps|CI/CD|SRE]
Phase: [DEFINE|PLAN|BUILD|VERIFY|REVIEW|SHIP]
```

## Phase-Specific Prompts

### DEFINE — PO + BA

```text
Goal: [user outcome in one line]
Scope:
  In MVP: [...]
  Out of MVP: [...]
Do now: [single discovery action — interview question, user call, competitor scan]
Do next: [/vibe-spec when DEFINE gate passes]
Done definition: [product brief approved, MVP boundary locked]
Risks / blockers: [stakeholder conflict, missing access, unclear user]
Assumptions: [labeled list]
Owner: PO
```

### SPEC — BA + PO

```text
Goal: [spec name + version]
Scope: [features in this spec]
Do now: [write or update PRD section X]
Do next: [remaining spec sections or /vibe-plan]
Done definition: [all stories have Given/When/Then acceptance criteria]
Risks / blockers: [ambiguous rules, missing integrations]
Assumptions: [tech or business assumptions surfaced]
Owner: BA
```

### PLAN — PM + SA

```text
Goal: [implement feature X from spec vY]
Scope: [tasks in this sprint/milestone]
Do now: [first task ID + owner Dev]
Do next: [task IDs in dependency order]
Done definition: [all tasks have acceptance + verify + ≤5 files]
Risks / blockers: [dependency, env, skill gap]
Assumptions: [architecture choices pending ADR]
Owner: PM
```

### BUILD — Dev

```text
Goal: [task ID: description]
Scope: [files/modules in this slice only]
Do now: [implement + test command]
Do next: [commit → next task or /vibe-test]
Done definition: [acceptance criteria met, tests pass, build green]
Risks / blockers: [spec gap, flaky test, merge conflict]
Assumptions: [implementation choices within task scope]
Owner: Dev
```

### VERIFY — QA

```text
Goal: [verify task/release X]
Scope: [test levels executed]
Do now: [run test suite / manual case Y]
Do next: [file bugs or sign off → /vibe-review]
Done definition: [all P0 acceptance criteria traced to passing tests]
Risks / blockers: [env down, missing data, flaky e2e]
Assumptions: [test env matches prod config]
Owner: QA
```

### REVIEW — Tech Lead

```text
Goal: [review PR/change set X]
Scope: [files in diff]
Do now: [five-axis review — correctness, design, tests, security, maintainability]
Do next: [merge | request changes | split PR]
Done definition: [zero Blockers, spec/task linked]
Risks / blockers: [missing tests, scope creep, security]
Assumptions: [reviewer context loaded]
Owner: Tech Lead
```

### SHIP — DevOps + CI/CD + SRE

```text
Goal: [deploy version X to environment Y]
Scope: [services affected]
Do now: [pipeline step or deploy command]
Do next: [smoke test → monitor → PO sign-off]
Done definition: [prod healthy, rollback tested, alerts live]
Risks / blockers: [quota, migration, downtime window]
Assumptions: [feature flags, canary %, maintenance window]
Owner: DevOps
```

## Handoff Block (attach after every card)

```text
HANDOFF: [FROM] → [TO]
Artifact: [path or doc name]
Decisions locked: [...]
Open questions: [...]
Gate status: [PASS | FAIL — reason]
```

## Squad Status Block (top of every reply)

```text
SQUAD: VibeCoding
Phase: [DEFINE|PLAN|BUILD|VERIFY|REVIEW|SHIP]
Active: [roles]
Lead: [role]
Command: [/vibe-*]
Task/Slice: [ID or name]
```