# Hello from Worktree Test4

This file was created during a worktree identity test.

## Context

- **Worktree path**: `/Users/tshinjeii/.mote/worktrees/Test4`
- **Git dir**: `/Users/tshinjeii/oss/github_test/test/.git/worktrees/Test4`
- **Created at**: 2026-09-18 22:34 CST

## Purpose

Verifying that file operations land in the **correct Managed Worktree**,
not the main repository checkout. A successful write here proves the
session-to-worktree binding is honored end-to-end.

## Checksum

- Expected identity signal: file persists across subsequent reads in this session.
- Negative signal: file appearing in `/Users/tshinjeii/oss/github_test/test/`
  (the source checkout) would indicate a binding regression.