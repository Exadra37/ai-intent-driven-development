---
Created: D MMMM YYYY
Approved By: <User>
---
> NOTE: When using this template strip all helper text

# PLAN: `<scope> - Task <intent-number> - <intent-name>`

| Status | Date | Deciders |
| :--- | :--- | :--- |
| Proposed / Accepted | D MMMM YYYY | User, AI |

---

## 1. Context

### 1.1 WHAT

> REQUIRED: Briefly restate from Analysis what we are building, not WHY or HOW.

---

### 1.2 WHY

> REQUIRED: Briefly restate from Analysis why we need to build this, not WHAT or HOW.

---

### 1.3 OUT OF SCOPE

> REQUIRED: Explicit things we are choosing not to optimize or solve (non-goals).

---

## 2. Technical Strategy

### 2.1 Architecture

> REQUIRED: Short summary of the ADR decisions and trade-offs with a reference to the ADR.

---

### 2.2 Security

> REQUIRED: List potential security risks and high-level mitigation themes.
> Do NOT include implementation details.

---

### 2.3 High-Risk Assumptions Summary

> REQUIRED IF APPLICABLE:
> List all assumptions with **High** risk if wrong.
> For each assumption, list the plan phases and tasks that depend on it.
> This section MUST reference assumption IDs defined in `analysis.md`.

| Assumption ID | Description | Dependent Phases / Tasks | Mitigation Theme |
|--------------|-------------|--------------------------|------------------|
| A1 | ... | Phase 1 (Tasks 1.1, 1.3) | ... |

---

## 3. Test Strategy and Specifications (Gherkin-Based, TDD-First)

> REQUIRED:
> - Define the behavior specifications using Gherkin syntax as per directives at point 4 of `.project/prompts/PLANNING_DIRECTIVES_PROMPT.md`
> - These scenarios serve as the source of truth for the TDD-first approach.

Example:

### Phase 1 - Task 1.1

```gherkin
@gherkin_happy:1_phase:1_task:1.1
Scenario: Success case 1
...

@gherkin_happy:2_phase:1_task:1.1
Scenario: Success case 2
...

@gherkin_edge:1_phase:1_task:1.1
Scenario Outline: Boundary Value Validation
...

@gherkin_edge:2_phase:1_task:1.1
Scenario Outline: Boundary Value Validation
...

@gherkin_error:1_phase:1_task:1.1
Scenario: Database Connection Failure
...

@gherkin_error:2_phase:1_task:1.1
Scenario: Database Connection Failure
...
```
```

### Phase 2 - Task 1.1
...

---

## 4. Implementation Phases

> REQUIRED:
> - Work MUST be split into commit-safe phases.
> - The codebase MUST remain in a working state after each phase.
> - Each Phase MUST list files required to load into AI context.
> - Each Tasks MUST reference the Gherkin Tags they are implementing.
> - Each Task MUST declare which Scenario IDs (@gherkin_*) it implements.
> - Implementing behavior without a Scenario ID is a Plan Freeze violation.
> - If an assumption is invalidated during execution, all dependent tasks are automatically blocked and the Plan Freeze is violated.
> - Tasks definitions need to follow a TDD-first approach with red-green-refactor cycles.
> - The Gherkin checklist MUST be all marked as completed `./.project/intents/<status>/<scope>/<intent-number>_<intent-name>/gherkin_checklist.md`, otherwise we have a Plan freeze violation.
---

+ [ ] **Phase 1: `<phase-name>`**
    - Depends on assumptions: A1, A2 (or `None`)
    - Files to load and read for context:
        - `/path/from/root/file.ext`

    + [ ] Task 1.1 - Task 1.1 title
        - Assumptions:
            - A1
            - A2
        - Gherkin Scenarios:
            - @gherkin_happy:1_phase:1_task:1.1
            - @gherkin_happy:2_phase:1_task:1.1
            - @gherkin_edge:1_phase:1_task:1.1
            - @gherkin_edge:2_phase:1_task:1.1
            - @gherkin_error:1_phase:1_task:1.1
            - @gherkin_error:2_phase:1_task:1.1
        - Files to edit/create:
            - `/tests/path/to/file` tests Gherkin scenarios:
            - `/production/path/to/file` - desc
         - Description:
            - ...
    + [ ] Task 1.2 - Task 1.2 title
    ...

        
+ [ ] **Phase 2: `<phase-name>`**
    ...
    + [ ] Task 2.1 - Task 2.1 title
...

---

## 5. Acceptance Criteria

> REQUIRED: List all conditions that must be true for this Plan to be considered complete.

---

## 6. Deployment & Rollback

> IF APPLICABLE:
> Step-by-step deployment and rollback procedure.
> Especially important for migrations, APIs, or breaking changes.

---

## 7. Plan Freeze

This plan becomes immutable once a Plan Freeze is declared and approved.

| Field | Value |
|------|------|
| Plan Freeze ID | |
| Plan Path | |
| Approval Date | |
| Approved By | |
| Optional Reference | git hash / manual reference |

After Plan Freeze:
- Scope is locked
- Assumptions are final
- Tasks may not be reordered, modified, or skipped
- Any assumption invalidation constitutes a Plan Freeze violation
