# /vibe-build

**Phase:** BUILD  
**Lead:** Dev | **Support:** SA, UX

Implement one vertical slice with tests and atomic commit.

Load skill: `vibecoding-squad-gsd`  
Playbook: `references/command-playbooks.md` → /vibe-build

**User prompt template:**

```text
/vibe-build

Task: [T-001 or description]
Spec/plan: [path]
Repo: [path]
```

**Auto mode:**

```text
/vibe-build auto

Plan: [approved task list]
Approve: I approve implementing all tasks with per-slice verification.
```

**Output:** Code + tests + BUILD GSD card + handoff to /vibe-test