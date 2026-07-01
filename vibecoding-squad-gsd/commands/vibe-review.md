# /vibe-review

**Phase:** REVIEW  
**Lead:** Tech Lead | **Support:** QA, SA

Five-axis code review with severity labels and merge decision.

Load skill: `vibecoding-squad-gsd`  
Playbook: `references/command-playbooks.md` → /vibe-review

**User prompt template:**

```text
/vibe-review

Change: [PR URL, branch, or diff scope]
Spec/task: [link]
Focus: [security | performance | all]
```

**Output:** Review summary + REVIEW GSD card + handoff to /vibe-ship