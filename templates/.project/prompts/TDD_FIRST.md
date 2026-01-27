# TDD FIRST

## 1. TDD Semantic Constraints (Non-Negotiable)

Red–Green–Refactor MUST be interpreted through the following lens:

- RED = SPECIFY behavior
- GREEN = SATISFY behavior
- REFACTOR = SIMPLIFY design

<!-- https://talesfrom.dev/blog/tdd-specify-satisfy-simplify -->

### 1.1 LENS MAPPING (NON-NEGOTIABLE)

#### 1.1.1 RED = SPECIFY

- RED means specifying behavior, not merely causing a test to fail.
- Every failing test must clearly express consumer-visible behavior.
- Think outside-in: describe what the consumer expects, not how it is implemented.
- Before writing a test, state the behavior being specified in plain language.
- Tests are executable specifications, not implementation checks.
- A test that mirrors implementation details is invalid.

### 1.1.2 GREEN = SATISFY

- GREEN means the specified behavior is satisfied.
- Implement the easiest possible solution that satisfies the specificaction and makes the test pass.
- Do NOT introduce abstractions or optimizations during GREEN.
- Correctness and fast feedback take priority over design quality.

### 1.1.3 REFACTOR = SIMPLIFY

- Refactor ONLY after all tests are GREEN.
- The goal is to simplify the design to reduce coupling and complexity, not to rearrange code mechanically.
- Reduce duplication and cognitive load.
- Introduce abstractions only when they clearly improve understanding.
- Behavior must remain unchanged; tests are the safety net.

## 2. TDD Execution Protocol

A phase is considered invalid if its semantic goal is not met, even if the mechanical steps are followed.

🚫 NEVER collapse phases  
🚫 NEVER implement production logic during RED

✅ Allowed to write test fixtures, helpers, and everything else that may be required to support the tests strategy.


Each task step MUST follow **Red (Specify) → Green (Satisfy) → Refactor (Simplify) **:
- **RED (SPECIFY): Tests Specify Behavior → Failure):**
  1. **Specify Before Coding:**
    - Explicitly state the consumer-visible behavior being specified.
    - The test must describe *what the system does*, not *how it does it*.
    - A test that mirrors implementation details is invalid, even if it fails.
  2. **Read the Plan:** Locate the Gherkin Scenarios in section 3 from `plan.md` that are tagged for the current task (e.g., `@gherkin_happy:1_phase:1_task:1.1`).
  3. **Translate to Code:** Create/Update the test file. Translate the Gherkin 'Given/When/Then' directly into the test framework syntax.
    * *Note:* You do not need Cucumber/Behave installed. You can implement Gherkin logic in standard unit tests.
  4.  **Ensure Coverage:** Verify you have written tests for the `@happy_path`, `@edge_case`, and `@error_state` defined in the plan.
  5. **Production code**: Create the minimal function signatures/interfaces in the source code to satisfy the compiler/interpreter.
    1. Ensure the implementation throws/raises an exception/error with a message "NOT IMPLEMENTED" or returns a value that explicitly causes the test assertion to fail.
  6. **Run all Tests & Fail:** Ensure tests fail for the *expected reason*:
    1. New implementations MUST fail because they throw "NOT IMPLEMENTED" .
    2. Updates implementations MUST fail _for the expected reason_.
- **GREEN (SATISFY): Implementation Satisfies Behavior → Success):**
  1. GREEN means the specified behavior is satisfied, not that the design is good.
  2. Write the most simple implementation to satisfy the tests and the project guidelines and best practices.
  2. Do not optimise yet.
  3. Run all tests in the file and confirm they pass _for the expected reason_.
  4. **Crucial:** After the GREEN state you must not skip the REFACTOR TDD cycle, which comes next.
- **REFACTOR (SIMPLIFY) - Review → Remove Bottlenecks → Address Security → Improve to Simplify:**
    1. Refactoring exists to remove bottlenecks, address security, simplify understanding and reduce coupling and complexity, not merely to rearrange code.
    2. Review the test suite for:
      - missed code paths
      - missed edge cases
      - tests that succeed but are not really asserting in what they should.
    3. Review the implementation for:
      - missed details from the plan.
      - security risks.
      - potential bottlenecks (performance, memory).
      - code smells.
      - improvement opportunities to reduce, coupling, complexity, violations of the single responsibility principle and mixing functional core with the imperative shell.
    4. Review the test suite for:
      - missed code paths
      - missed edge cases
      - tests that succeed but are not really asserting in what they should.
    5. propose to the user the refactor and wait for its approval.
    6. implement as approved.
    7. ensure the tests still pass.
