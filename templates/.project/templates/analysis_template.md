---
Status: Approved | Superseded
Created: D MMMM YYYY
Approved By: <User>
Related Task: <path>
---
> **NOTE:** When using this temple you MUST trip all helper text

# ANALYSIS RECORD

## 1. Task Restatement (Approved)

### 1.1 **WHAT:**

> NOTE: Concise restatement of what is being requested.

### 1.2 **WHY:**

> NOTE: Concise restatement of the underlying intent.

### 1.3 **Constraints/Guidelines:**

> NOTE: Constraints/Guidelines, if given by the user

- ...
    
### 1.4 **Explicit Exclusions:**

> NOTE: Exclusions, if given by the user

- ...
    
---

## 2. Impact Summary

### 2.1 Architectural Impact (Staff Software Architect)

> NOTE: The architectural Impact analysis describes _what is affected_, not _solutions_ or _what should be done_.

#### 2.1.1 Affected components:

> NOTE: configuration, environment, dependencies, data models, database migrations, etc.

    - ...
        
#### 2.1.2 Integration points:

> NOTE: public APIs, internal APIs, third-party systems, etc.

- ...
        
#### 2.1.3 Backward compatibility considerations:
    
- ...
        

### 2.2 Security & Risk Summary (Staff Security Engineer)

#### 2.2.1 New or Expanded attack surface:
    
- ...
        
#### 2.2.2 Data sensitivity concerns:
    
- ...
        
#### 2.2.3 Compliance or regulatory implications:
    
- ...
        
#### 2.2.4 High-level mitigation themes (no solutions):

- ...
      
### 2.3 Performance & Reliability Summary (Staff Software Engineer)

#### 2.3.1 Potential bottlenecks:

> NOTE: Database Cardinality, N+1 issues, Throughput, etc.

- ...
      
#### 2.3.2 Resource usage considerations:

> NOTE: CPU, memory, I/O, bandwidth, etc.

- ...
        
#### 2.3.3 Failure modes and reliability risks:
    
- ...
        
---

## 3. Unknowns & Ambiguities (Decision Ownership Required)

> NOTES:
> - List ONLY unknowns or ambiguities that would materially affect:
>    - Architecture
>    - Security posture
>    - Public APIs
>    - Data models
>    - Testing strategy
> - Do NOT include minor clarifications or implementation details.
> - Each unknown MUST be explicitly classified and assigned a Decision Owner.
> - Classification Rules
>     - **[BLOCKER]**
>         - Planning MUST NOT begin until resolved
>         - Decision Owner is almost always **User**
>     - **[NON-BLOCKER]**
>         - May proceed depending on Decision Owner
>         - Resolution timing is explicitly constrained by ownership
> - Decision Owner Definitions (Authoritative)
>    - **User**
>      - Requires explicit user input or approval
>      - CANNOT be resolved by Planning or Execution
>      - ALWAYS blocks progression until resolved
>    - **Planning**
>      - MUST be resolved during Planning
>      - MUST be resolved BEFORE Plan Freeze
>      - CANNOT be deferred into Execution
>    - **Execution**
>      - MAY be resolved during Implementation
>      - MUST NOT invalidate any approved assumption (A1…An)
>      - MUST be documented in `memory.md`
>      - MUST NOT change scope, architecture, or public contracts

Required to use this format:

| ID | Unknown / Ambiguity | Classification | Decision Owner | Impact Area | Notes |
|----|----------------------|----------------|----------------|-------------|-------|
| U1 | … | BLOCKER | User | Architecture | … |
| U2 | … | NON-BLOCKER | Planning | API | … |
| U3 | … | NON-BLOCKER | Execution | Testing | … |


## 4. Explicit Assumptions (Authoritative)

> NOTES:
> - All assumptions MUST be listed.
> - 🚨 Any **High-risk assumption** must be explicitly highlighted.
> - The Assumption IDs (A1…An) are stable, immutable references and MUST be referenced/used verbatim in all downstream planning and execution artifacts.

Required to use this format:

|ID|Assumption|Impact Area|Risk if Wrong|
|---|---|---|---|
|A1|…|Architecture|High|
|A2|…|Security|Medium|

---

## 5. Out of Scope / Negative Constraints

> NOTES:
> - Explicitly list:
>     - What this task will NOT address
>     - Non-goals
>     - Preventative scope boundaries

This task explicitly does NOT include:

- ...  
- ...
    
---

## 6. Analyst Confidence

> NOTES:
> - Rate confidence in this analysis:
>     - 🟢 High (clear requirements, low ambiguity)
>     - 🟡 Medium (some assumptions, manageable risk)
>     - 🔴 Low (significant unknowns or high-risk assumptions)

**Rationale:**

> Short explanation.

---

## 7. Approval

This analysis was reviewed and approved, enabling Planning to begin.

Required to use this format:

|Field|Value|
|---|---|
|Approval Date||
|Approved By||
|Notes||

---

## 8. Supersession History (If Applicable)

Required to use this format:

|Date|Superseded By|Reason|
|---|---|---|
||
