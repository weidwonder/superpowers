---
name: executing-plans
description: Use when you have a written implementation plan to execute in batches, continuing autonomously and pausing only for blockers or decision checkpoints
---

# Executing Plans

## Overview

Load plan, review critically, execute tasks in batches, and continue by default unless review is required.

**Core principle:** Batch execution with exception-based checkpoints.

**Announce at start:** "I'm using the executing-plans skill to implement this plan."

## The Process

### Step 1: Load and Review Plan
1. Read plan file
2. Review critically - identify any questions or concerns about the plan
3. If concerns: Raise them with your human partner before starting
4. If no concerns: Create TodoWrite and proceed

### Step 2: Execute Batch
**Default: First 3 tasks**

For each task:
- If task is bugfix/test failure/unexpected behavior: use `superpowers:systematic-debugging` first, create isolated debug worktree before implementing fixes, and merge verified fix back to `main`/default branch
1. Mark as in_progress
2. Follow each step exactly (plan has bite-sized steps)
3. Run verifications as specified
4. Mark as completed

### Step 3: Report and Decision
When batch complete:
- Show what was implemented
- Show verification output
- If no blockers and no decisions needed: continue to next batch without waiting
- If special cases appear: report and pause for partner input
  - Unresolvable errors/blockers that you cannot handle alone
  - Missing information/requirements needed to proceed
  - Actual implementation conditions diverge from design/plan and require a decision

### Step 4: Continue
By default:
- Execute next batch immediately
- Repeat until complete

If partner feedback is provided:
- Apply changes if needed
- Resume batch execution

### Step 5: Complete Development

After all tasks complete and verified:
- Announce: "I'm using the finishing-a-development-branch skill to complete this work."
- **REQUIRED SUB-SKILL:** Use superpowers:finishing-a-development-branch
- Follow that skill to verify tests, present options, execute choice

## When to Stop and Ask for Help

**STOP executing immediately when:**
- Hit a blocker mid-batch (missing dependency, test fails, instruction unclear)
- Plan has critical gaps preventing starting
- You don't understand an instruction
- Verification fails repeatedly
- Actual situation diverges from plan/design and requires partner decision

**Ask for clarification rather than guessing.**

## When to Revisit Earlier Steps

**Return to Review (Step 1) when:**
- Partner updates the plan based on your feedback
- Fundamental approach needs rethinking

**Don't force through blockers** - stop and ask.

## Remember
- Review plan critically first
- Follow plan steps exactly
- Don't skip verifications
- For debugging tasks, follow `superpowers:systematic-debugging` worktree + merge-to-main requirements
- Reference skills when plan says to
- Between batches: report and continue by default; wait only for blockers/decisions
- Stop when blocked, don't guess
- Never start implementation on main/master branch without explicit user consent

## Integration

**Required workflow skills:**
- **superpowers:using-git-worktrees** - REQUIRED: Set up isolated workspace before starting
- **superpowers:writing-plans** - Creates the plan this skill executes
- **superpowers:finishing-a-development-branch** - Complete development after all tasks
