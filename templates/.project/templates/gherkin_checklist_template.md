# Gherkin Coverage Checklist

> This checklist MUST be completed before a task enters Implementation.
> Incomplete or unchecked items block execution.

---

## 1. Acceptance Criteria Coverage

| Acceptance Criterion ID | Covered by Scenario(s) | Scenario ID(s) | Status |
|------------------------|------------------------|----------------|--------|
| AC-1 | Yes / No | @gherkin_happy:1_phase:1_task:1.1 | [ ] |
| AC-2 | Yes / No | @gherkin_edge:1_phase:1_task:1.1, @gherkin_edge:2_phase:1_task:1.1 | [ ] |

- [ ] All Acceptance Criteria are covered by ≥at least one scenario
- [ ] No scenario lacks a task
- [ ] No acceptance criterion lacks a scenario
      
---
u
## 2. Happy Path Coverage

- [ ] At least one **happy-path** scenario exists  
- [ ] Happy-path scenarios describe **externally observable outcomes only**  
- [ ] No happy-path scenario includes error handling or edge logic  
- [ ] Each happy-path scenario asserts exactly one primary success behavior  

---

## 3. Edge Case Coverage

- [ ] Boundary conditions are explicitly identified  
- [ ] Each edge case is covered by **its own scenario**  
- [ ] No scenario combines multiple edge cases  
- [ ] Edge cases are valid inputs or states (not errors)

List identified edge cases:
- EC-1:
- EC-2:

---

## 4. Error State Coverage

- [ ] Invalid input cases are covered  
- [ ] Unauthorized / forbidden actions are covered (if applicable)  
- [ ] Invariant violations are covered (if applicable)  
- [ ] Each error scenario asserts:
    - [ ] Rejection behavior
    - [ ] Explicit error code or error type
    - [ ] No unintended state changes

---

## 5. Scenario Quality Checks

- [ ] Each scenario tests **one behavior only**  
- [ ] Scenarios are independent and order-agnostic  
- [ ] No scenario relies on shared mutable state  
- [ ] No implementation details appear in Given/When/Then  
- [ ] All outcomes are deterministic and verifiable  

---

## 6. TDD Readiness

- [ ] Each scenario can be mapped to test cases  
- [ ] Tests can be written without production code existing  
- [ ] Expected failure mode in RED phase is clear  
- [ ] GREEN implementation can be minimal and scoped  

---

## 7. Final Declaration

By checking all items above, this task is declared:

- ✔ Ready for TDD-first implementation
- ✔ Safe to enter Plan Freeze
- ✔ Fully specified from a behavior perspective

| Field | Value |
|------|------|
| Reviewed By | |
| Date | |
| Notes | |
