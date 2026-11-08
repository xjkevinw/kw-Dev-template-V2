```
# Development Process &amp; Workflow Specification

## 1. Task Backlog Rules
- Tasks are tracked as GitHub Issues (or local issue specifications).
- Tasks are executed one at a time per agent loop.
- Every task must be groomed before any code implementation starts.
- Always commit work regularly after achieving meaningful progress or passing a test milestone.

## 2. Team Roles &amp; Responsibilities
- **Product Manager (PM)**: Grooms tasks before implementation. Follows `_docs/team/pm.md` and uses `_docs/task-template.md`.
- **Software Engineer (SWE)**: Implements groomed tasks against acceptance criteria. Follows `_docs/team/software-engineer.md`.
- **QA Engineer (QA)**: Independently verifies implementation against acceptance criteria. Follows `_docs/team/qa-engineer.md`.

## 3. Orchestrator Lifecycle (Graph Workflow)
The Orchestrator session dispatches sub-agents (PM, SWE, QA) to process issues autonomously:

1. **Pick Issue**: Select the next open issue from the backlog.
2. **Grooming Phase**: PM Agent grooms the task, ensuring checkable Acceptance Criteria and clear Out-of-Scope boundaries.
3. **Implementation Phase**: Software Engineer Agent writes code and unit/integration tests.
4. **Verification Phase**: QA Agent independently tests the implementation and outputs a binary verdict (`PASS` or `FAIL`).
5. **Feedback Loop**:
   - On `FAIL`: Return to Step 3 with QA error logs and feedback as input.
   - On `PASS`: Orchestrator closes the issue.
6. **Stop Condition**: Repeat until the target backlog is empty or all specified issues pass QA.

## 4. Execution Rules &amp; Boundaries
- The Engineer must NOT change the acceptance criteria.
- The Engineer must NOT close the issue directly.
- The QA Engineer must NOT modify any code — only report test verdicts.
- The Orchestrator closes the issue ONLY after receiving an explicit `PASS` verdict from QA.

```
