# Open Questions Document — <PBI ID>

Document for resolving blockers, risks, and inconsistencies detected across specs.
Simply mark the chosen option with `[x]` (or fill in `Other:`).
The agent will automatically fill in the final Summary table and update the corresponding spec files.

---

## Blockers — must be resolved before implementation

---

### B1 — spec-NN: <Issue title>

**Context:** <One or two sentences explaining the problem and its concrete consequence if left unresolved.>

**Options:**

- [ ] **A)** <Concrete option with brief technical implications>
- [ ] **B)** <Concrete option with brief technical implications>
- [ ] **C)** <Concrete option with brief technical implications>

- [ ] **Other:** ______

**Notes:**

---

## Risks — may cause rework if not resolved

---

### R1 — spec-NN: <Issue title>

**Context:** <One or two sentences explaining the problem and its concrete consequence if left unresolved.>

**Options:**

- [ ] **A)** <Concrete option with brief technical implications>
- [ ] **B)** <Concrete option with brief technical implications>
- [ ] **C)** <Concrete option with brief technical implications>

- [ ] **Other:** ______

**Notes:**

---

## Minor inconsistencies

---

### M1 — spec-NN: <Issue title>

**Context:** <One or two sentences explaining the problem and its concrete consequence if left unresolved.>

**Options:**

- [ ] **A)** <Concrete option with brief technical implications>
- [ ] **B)** <Concrete option with brief technical implications>
- [ ] **C)** <Concrete option with brief technical implications>

- [ ] **Other:** ______

**Notes:**

---

## Summary

| ID | Spec  | Impact  | Short description                  | Decision |
|----|-------|---------|------------------------------------|----------|
| B1 | NN    | Blocker | <one-line description>             | ___      |
| R1 | NN    | Risk    | <one-line description>             | ___      |
| M1 | NN    | Minor   | <one-line description>             | ___      |

---

## Authoring rules

- **ID convention:** `B<n>` = blocker, `R<n>` = risk, `M<n>` = minor inconsistency.
- **Always include `Other:`** as an open field — never force a choice between inadequate options.
- **Max 4 predefined options** per item; if more exist, group the least likely ones.
- **Context must state the consequence** of not resolving, not just describe the problem.
- **Options must be mutually exclusive and actionable** — avoid vague options like "ask the TL" as the only choice.
- **Update the spec and summary table**: Once the user checks an option with `[x]`, the agent will automatically update the corresponding spec and fill in the decision in the Summary table.

---

## Real example (from PBI-1)

### B4 — spec-02/03: Java type of `FECHA_DOCUM` never defined

**Context:** spec-02 maps `FECHA_DOCUM` to `InformesReportingRowDTO` and spec-03 extracts the month and year
from that field. No spec defines what Java type `IAlveoDatabaseProvider` returns for it.
If it arrives as `java.sql.Date` or `Timestamp`, the `substring("2024-03-15", 0, 4)` in Scenario 7
fails at runtime. Both the month mapper (Enero–Diciembre) and the year mapper depend directly on this type.

**Options:**

- [ ] **A)** Assume `String` in `"YYYY-MM-DD"` format (JdbcTemplate default for Oracle 12c DATE columns without time)
- [ ] **B)** Assume `java.sql.Date`; the mapper converts to `LocalDate` before extracting month and year
- [ ] **C)** Assume `java.sql.Timestamp`; the mapper converts to `LocalDate` before extracting month and year
- [ ] **D)** Check how the legacy MD06 code handles that field today and replicate the type

- [ ] **Other:** ______

**Notes:**
