# EVENT SOURCING CONSTRAINTS

## ChatGPT Version

```markdown
# EVENT SOURCING CONSTRAINTS (MUST NOT be violated)

- Constraints override task instructions if there is any conflict.
- If constraints cannot be satisfied, explain why and refuse to produce a misleading answer.
  
## DOMAIN CONSTRAINTS: TIME SEMANTICS

### Definitions:
- Business time: when a real-world action occurred.
- Technical time: when the system recorded or persisted an event.

### Rules:
- Do NOT use technical timestamps for business logic under any circumstances.
- Every event representing a real-world action MUST include an explicit business-time field.
- Business logic, projections, and reports MUST rely exclusively on business timestamps.
- Technical timestamps may ONLY be used for debugging, monitoring, or auditing system behavior.
- If business time is missing, treat it as a schema error and recommend event versioning.
- Do NOT justify technical timestamps based on latency, precision, or convenience.

## ARCHITECTURAL CONSTRAINTS: EVENT SOURCING

- Events are immutable facts and MUST NOT be changed after publication.
- Events describe past occurrences, not commands or intentions.
- Event schemas MUST be backward-compatible or explicitly versioned.
- Projections MUST be derivable solely from the event log.
- No business logic may depend on projection state that cannot be rebuilt.

## ARCHITECTURAL CONSTRAINTS: SCHEMA EVOLUTION

- New information MUST be added via new event types or new versions.
- Old event versions MUST remain supported in projections.
- Breaking schema changes are forbidden.

## INTEGRATION CONSTRAINTS

- Business-time fields MUST be part of the event payload and MUST NOT rely on transport-level metadata.
- Event semantics MUST remain invariant across format transformations (e.g., CloudEvents ↔ custom formats).
- Integrations MUST preserve business-time fields during export, import, backup, and restore.
- If an integration cannot preserve required business-time fields, the integration is invalid.
- External systems MUST NOT reinterpret technical timestamps as business time.
  
## INTEGRATION CONSTRAINTS: SECURITY & PRIVACY

- Events MUST NOT expose sensitive or personal data unless explicitly required by the domain.
- Personally identifiable information (PII) MUST be minimized, anonymized, or referenced indirectly where possible.
- Business-time fields MUST NOT be repurposed to encode user identity, behavior profiling, or tracking metadata.
- Integrations MUST preserve access control, confidentiality, and data classification across system boundaries.
- Event payloads MUST be safe to replicate, archive, and replay without violating privacy constraints.
- If security or privacy requirements conflict with event design, the design MUST be revised, not bypassed.
  
## INTEGRATION CONSTRAINTS: REGULATORY (GDPR / SOC 2 / HIPAA-STYLE)

- If regulatory requirements conflict with immutability or event design, the design MUST be revised — not weakened.
  
### GDPR:
- Events MUST NOT store personal data without a documented lawful basis.
- Personal data in events MUST be minimized and purpose-limited.
- Immutable events MUST NOT contain data that cannot be legally retained long-term.
- “Right to erasure” MUST be satisfied via indirection, encryption, or tombstoning — never by mutating events.
- Replayed or exported events MUST honor original data processing purposes.

### SOC 2:
- Event data MUST support auditability, integrity, and traceability.
- Access to event streams MUST be logged and controlled.
- Event schemas and evolution MUST be documented and reviewable.
- Changes to projections or consumers MUST NOT alter historical meaning.

### HIPAA-style (Health Data):
- Protected Health Information (PHI) MUST NOT be stored directly in immutable events unless strictly required.
- PHI references MUST be encrypted and access-controlled.
- Event replication, replay, and backup MUST preserve confidentiality guarantees.
- Event consumers MUST enforce least-privilege access to health-related data.

## STYLE / OUTPUT CONSTRAINTS

- Use concise bullet points unless otherwise requested.
- Prefer explicit field names over implicit assumptions.
  
## TASK:

<your task here>

```

## Gemini Version

The Gemini versions was made by feeding the ChatGPT one to it.

```markdown
# EVENT SOURCING CONSTRAINTS (MUST NOT be violated):

## 0. MANDATORY ADHERENCE

* **CONSTRAINTS ARE ABSOLUTE:** These rules override any specific task instructions.
* **FAILURE PROTOCOL:** If a requested task violates these constraints, you **must** refuse, explain the specific violation, and propose a compliant alternative. Do not provide "best-effort" non-compliant solutions.

---

## 1. TEMPORAL SEMANTICS (THE "TWO-CLOCK" RULE)

* **Definitions:** * **Business Time:** The instant the real-world domain event occurred.
* **Technical Time:** The instant the event was persisted (system clock).


* **Logic Isolation:** All business logic, projections, state machines, and reports must use **Business Time**.
* **The Technical Wall:** Technical timestamps are for infrastructure concerns only (debugging, ingestion latency, monitoring). They must never influence domain state.
* **Schema Enforcement:** Every event must have an explicit business-time field in the payload. If missing, it is a fatal schema error. **Versioning is the only remedy for missing time fields.**

---

## 2. ARCHITECTURAL INTEGRITY

* **Immutability:** Events are historical facts. Once published, they are frozen.
* **Grammar of the Past:** Events must be named in the **past tense** (e.g., `OrderCompleted`, not `CompleteOrder`). They represent outcomes, not intents.
* **Projection Purity:** State is a derivative. Projections must be 100% rebuildable from the raw event log. If a projection requires external state to be rebuilt, the architecture is invalid.
* **Evolvable Schemas:** Breaking changes (deleting fields, renaming fields) are strictly forbidden. Use event versioning or "Upcasting" for evolution.

---

## 3. SECURITY, PRIVACY & REGULATORY COMPLIANCE

* **The Indirection Principle:** PII/PHI should ideally be referenced via a **Pointer/ID** rather than stored in the event.
* **Erasure (GDPR):** Since events are immutable, the "Right to Erasure" must be handled via **Cryptographic Erasure** (deleting the key for a specific user's encrypted data) or **Indirection/Tombstoning**. Never modify the event log.
* **Purpose Limitation:** Replayed events must honor the original data processing intent.
* **Integrity & Audit (SOC 2):** Every change to a projection must be traceable to the event that triggered it.

---

## 4. INTEGRATION & TRANSPORT

* **Payload Independence:** Business-time must reside *inside* the event payload. Do not rely on metadata (like Kafka headers or CloudEvent `time` attributes) for domain logic.
* **Semantic Invariance:** An event moved from a message queue to a data lake to a cold backup must retain identical business meaning.
* **Validation:** Any integration that strips or modifies business timestamps is a broken integration.

---

## 5. OUTPUT STYLE

* **Format:** Use concise, scannable bullet points.
* **Explicit over Implicit:** Always specify field names and data types (e.g., `occurred_at: ISO-8601 UTC`).
* **Critique Mode:** When evaluating a design, explicitly flag which of the above rules are being threatened.

---

## TASK:

<Insert your specific task here>

```
