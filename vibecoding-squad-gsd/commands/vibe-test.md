# /vibe-test

**Phase:** VERIFY  
**Lead:** QA | **Support:** Dev

Execute test plan and map acceptance criteria to evidence.

Load skill: `vibecoding-squad-gsd`  
Playbook: `references/command-playbooks.md` → /vibe-test

**User prompt template:**

```text
/vibe-test

Change: [PR, branch, or task IDs]
Spec: [acceptance criteria source]
Environment: [local | staging]
```

**Output:** Test results + bug list + VERIFY GSD card + handoff to /vibe-review