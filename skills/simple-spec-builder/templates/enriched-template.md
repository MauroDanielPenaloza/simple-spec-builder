# User Story – Enriched Template

Use this template when documenting stories under **`.tasks/<ticket>/`** (e.g., `PBI-24287`; the identifier varies).  
**File conventions (same ticket folder):**

| File | Purpose |
|---------|-----------|
| `index-spec.md` | Index: sources, execution order, dependencies between specs, global field-to-field mapping if applicable. |
| `spec-<NN>-<kebab-name>.md` | One story/vertical slice per file; `<NN>` = `01`, `02`, … |
| `open-questions.md` | Log of business decisions and technical or blocking questions. |
| `solution-diagrams.md` | Mandatory technical diagrams of the solution (sequence, class, and other supporting diagrams). |

**Language:** Stories and Gherkin **in English** by default (team); headers can follow the functional template in English (recommended).

---

## File Template — `spec-<NN>-*.md`

Copy sections that apply; omit empty ones.

---

### `# User Story Description`

A short paragraph (what problem this slice solves and how it fits into the epic).

---

### `# Story (INVEST)`

```
**As** …  
**I want** …  
**So that** …
```

---

### `# Analysis`

#### Approach

Brief text: solution strategy (vertical slice), assumptions, explicit in-scope / out-of-scope.

#### API Controller (this spec)

`Method | Route | Purpose` table, then JSON snippets:

- Request (when applicable): `Content-Type`, example `application/json`.
- Response (expected status codes based on current controller).
- **Input validations** (FluentValidation / DataAnnotations): optionality, lengths, types — without duplicating generic DoD.

---

### `# Starting Point`

Example table:

| | |
| -- | -- |
| **Project** | `current-project`, `Core`, etc. |
| **Classes** | File paths from repo root (`src/…`). |
| **Method / mapping** | Which method or AutoMapper profile to modify. |

---

### `# Context` (optional)

Relative links to `raw-definition.md`, `frontend-change-definition.md`, other specs (`spec-02-…`).

---

### `# Acceptance Criteria`

**Given / When / Then** scenarios (English recommended). First **happy path**, then **unhappy** / authorization / validation.

---

### `# Test Plan`

#### Context

What data, environment, or policies are required.

#### Scenarios

Numbered table: Success / Alternative success / Error / Regression.

---

### `# Post-implementation Validation`

Short list aligned with the repo, for example:

1. `mvn clean install`
2. `mvn test` in relevant test projects
3. Local startup and manual or functional test if applicable

---

### `# Non-functional notes`

Global NFRs (performance, policy security); **do not** include DoD (generic unit tests, code review) within the AC.

---

### `# Open questions` (optional)

Bullets if there is business ambiguity pending PO.

---

## Template — `index-spec.md`

```markdown
# <TICKET> — specification index

## Source artifacts

Table: file | purpose.

## Field mapping (contract ↔ Core) — when applicable

Summary table JSON ↔ DTO ↔ domain; links to each spec.

## Execution order

Table: Order | spec file | Summary | Depends on

## Suggested increments / Backbone

MVP narrative → enhancements (Story Mapping / Walking Skeleton).
```

Cross-reference to this template from the [simple-spec-builder](../SKILL.md) skill.
