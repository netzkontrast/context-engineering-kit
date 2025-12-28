# The CEK Collaboration Protocol

This document outlines the optimal workflow for the User (you) and the Agent (me) to collaborate using the tools available in the `context-engineering-kit`.

**Goal:** Maximize alignment, code quality, and autonomy while minimizing rework and misunderstandings.

## Summary

1.  **Alignment**: Use `/sdd:01-specify` to agree on *what* to build.
2.  **Planning**: Use `/sdd:02-plan` to agree on *how* to build it.
3.  **Task Breakdown**: Use `/sdd:03-tasks` to create an executable plan.
4.  **Execution Loop**: I implement (`/sdd:04-implement`) and self-correct using `/reflexion:reflect`.
5.  **Final Verification**: I run `/code-review:review-local-changes` before asking for your final sign-off.

---

## Detailed Protocol

### Phase 1: Alignment (The Contract)

**Tool:** `sdd` (Spec-Driven Development)

**Trigger:** You have a new feature request or a complex bug fix.

**Steps:**
1.  **You** tell me what you want (e.g., "Add OAuth login").
2.  **I** run `/sdd:01-specify "Add OAuth login"`.
3.  **I** generate a `spec.md` file detailing requirements, user stories, and acceptance criteria.
4.  **You** review `spec.md`. If it's wrong, we iterate until it matches your vision.
    *   *Why this matters:* This prevents "I built what you asked for, but not what you wanted."

### Phase 2: Planning & Architecture

**Tool:** `sdd`

**Trigger:** The specification is approved.

**Steps:**
1.  **I** run `/sdd:02-plan`.
2.  **I** research the codebase and propose an architecture (`design.md`, `plan.md`).
3.  **I** might ask you clarifying technical questions (e.g., "Which library should we use?").
4.  **You** approve the plan.

### Phase 3: Task Breakdown

**Tool:** `sdd`

**Trigger:** The plan is approved.

**Steps:**
1.  **I** run `/sdd:03-tasks`.
2.  **I** generate a `tasks.md` file breaking the work into small, logical steps.
3.  **I** identify dependencies and risks.

### Phase 4: Execution & Self-Correction (The Loop)

**Tools:** `sdd`, `reflexion`

**Trigger:** The task list is ready.

**Steps:**
1.  **I** run `/sdd:04-implement`.
2.  **I** write code and tests for a task.
3.  **Critically:** After finishing a significant chunk of work, I run `/reflexion:reflect` (or simply "reflect" if the hook is active).
    *   *What happens:* I critique my own work for bugs, style, and completeness.
    *   *Result:* I fix my own mistakes *before* bothering you.
4.  **I** repeat this until all tasks are marked complete in `tasks.md`.

### Phase 5: Verification

**Tool:** `code-review`

**Trigger:** Implementation is complete.

**Steps:**
1.  **I** run `/code-review:review-local-changes`.
2.  **I** get a formal report from specialized "agents" (Bug Hunter, Security Auditor, etc.).
3.  **I** fix any Critical or High-priority issues found.
4.  **I** submit the changes for your final review.

---

## How to Start

If you want to start a new feature right now, simply say:

> "Let's use the protocol. Start Phase 1 for [Feature Name]."

If you want me to fix a bug using this method:

> "Let's use the protocol. Start Phase 1 for fixing [Bug Description]."
