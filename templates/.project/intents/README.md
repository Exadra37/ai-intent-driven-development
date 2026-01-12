# PROJECT TRACKING

All work in this repository is tracked under the `.project/` directory, which serves as the **single source of truth** for intents, plans with tasks, decisions, and session memory.

## Folder Structure

### Canonical Folder Tree 

```text
./.project/intents
├── 0.last_task_created
├── README.md
└── <status>
    └── <type>
        └── <scope>
            └── <intent-number>_<intent-name>
                ├── adr.md
                ├── analysis.md
                ├── memory.md
                ├── plan.md
                └── user_request.md
```

### Intent Path Signature

The signature for the intent path is `./.project/intents/<status>/<type>/<scope>/<intent-number>_<intent-name>/`:
* `<status>` - one of : `draft`, `todo`, `work-in-progress`, `paused`, `completed`
* `<type>` - one of: `feature`, `bug`, `refactor`, `improvement`, `devops`, `chore` 
* `<scope>` - the domain or feature being worked on, e.g. `accounts`, `authentication-login`, `canvas`, etc.
* `<intent-number>` - the intent number is derived by adding `1` to the `<intent-number>`  from `.project/intents/<intent-number>.last_intent_created`, e.g. `10.last_intent_created`.
* `<intent-name>`: a short kebab-case name for the intent, not the the intent title, e.g `add-user-registration`

Some examples:   
+ `.project/intents/todo/feature/accounts/1_add-user-accounts/`
+ `.project/intents/draft/improvement/canvas/6_enhance-search-results/`
+ `.project/intents/work-in-progress/bug/12_fix-authentication-login/`

### Intent Folder Contents

Each intent folder **always** contains the following files:

| File              | Purpose                                                    |
| ----------------- | ---------------------------------------------------------- |
| `user_request.md` | Detailed request, written using `user_request_template.md` |
| `analysis.md`     | Analysis, using `analysisn_template.md`              |
| `plan.md`         | Implementation plan, using `plan_template.md`              |
| `adr.md`          | Architecture Decision Record, using `adr_template.md`      |
| `memory.md`       | Session memory and context, using `memory_template.md`     |

## Intent Tracking

Intent tracking is based on the Intent Folder structure at `./.project/intents/<status>` .

### Intent Lifecycle

Intents move status **by changing directories**, not by editing metadata. This move MUST be done with `git mv` to keep track of the differences.

#### Lifecycle Flow

```text
draft → todo → work-in-progress → completed
                ↓
              paused
```

#### Lifecycle Rules

+ **Draft**
  + Intent is still being clarified
  + Implementation may not be approved yet
+ **Todo**
  + Intent is well-defined and ready to be worked on
  + `analysis.md`, `plan.md`, `adr.md` and `memory.md` should be complete
+ **Work-in-progress**
  + Active development
  + `memory.md` should be updated as work progresses
+ **Paused**
  + Work temporarily stopped
  + Reason must be documented in `memory.md`
+ **Completed**
  + Implementation finished:
    + Tasks in `plan.md` all marked as completed
    + Code committed
    + Documented in `memory.md`
  + Code merged (optional)
