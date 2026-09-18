# Git Test — Worktree Test5

This file was created during a Git identity / binding drift test.

## Session Binding

- **Bound workspace**: `Test5`
- **Worktree path**: `/Users/tshinjeii/oss/github_test/.mote-worktrees/Test5`
- **Git dir**: `/Users/tshinjeii/oss/github_test/test/.git/worktrees/Test5`
- **Session ID**: `sess_ru7chgboqe9ha6pe`
- **Created at**: 2026-09-18 22:40 CST

## What This Test Verifies

Per long-term memory, Mote historically had **multiple copies of "current Git
state"** competing for authority
(`git_assignments.branch`, `local_branch_workflows.session_branch`,
frontend cache, etc.). The authoritative-source-of-truth rule is:

| Information type        | Single source of truth |
|-------------------------|------------------------|
| Git worktree identity   | **Physical state** (`git status`, `git branch --show-current`) |
| Workspace / Repository  | **Authorization** (session ↔ worktree binding) |
| Workflow                | **Operation intent** (declared step, not inferred) |

This file proves:

1. The session is correctly bound to **Test5** (not Test4, not main repo).
2. Writes land in the bound worktree's filesystem, not in
   `/Users/tshinjeii/oss/github_test/test/` (the source checkout).
3. Drift between `git_assignments.branch` ↔ `local_branch_workflows.session_branch`
   would surface as a permission/state error rather than silent overwrite.

## Drift Signal Inventory

- [ ] `git status` reports `?? git_test.md` only (no spurious changes elsewhere)
- [ ] Source checkout `/Users/tshinjeii/oss/github_test/test/` does **not** contain
      this file
- [ ] File persists across subsequent reads within this session
- [ ] If branch was switched by a concurrent workflow step, surface a
      drift warning to the user instead of silently writing