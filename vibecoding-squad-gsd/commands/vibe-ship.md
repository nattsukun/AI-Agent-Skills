# /vibe-ship

**Phase:** SHIP  
**Lead:** DevOps | **Support:** CI/CD, SRE, QA

Deploy with pipeline gates, smoke tests, rollback, and observability.

Load skill: `vibecoding-squad-gsd`  
Playbook: `references/command-playbooks.md` → /vibe-ship

**User prompt template:**

```text
/vibe-ship

Release: [version or branch]
Target: [staging | production]
Runbook: [path or paste]
Rollback tested: [yes | no]
```

**Output:** Deploy log + smoke results + SHIP GSD card + release notes