---
name: simple-spec-builder
description: >
  Generates, details, splits, and maps agile user stories. Applies INVEST, 5Cs, BDD/Gherkin, "Three Amigos" approaches, NFRs/DoD assessment, 10 Story Splitting strategies, and the User Story Mapping model (Backbone, Narrative Flow, Slicing), maximizing value (Outcome) over quantity (Output).
trigger: When the user requests to write a specification, spec, user story, write acceptance criteria, split an epic, manage technical debt, prioritize a backlog, or map the visual flow of a product.
license: Apache-2.0
metadata:
  author: mauro.penaloza
  version: "1.1"
---

#### When to Use

Use this skill when:

* The user describes a generic feature and asks to convert it into a formal user story.
* There is a need to transform an idea into structured and visually organized agile requirements.
* You need to visually map the complete user experience (User Story Mapping).
* A user story is too large (Epic) and needs to be split using advanced partitioning techniques.
* An existing user story lacks measurable Acceptance Criteria or needs to be structured in Gherkin.
* There is technical or functional uncertainty that requires a Spike, an independent technical story, or a functional Walking Skeleton.
* There is a lack of clarity on the real value a feature will bring to the business or customer.

--------------------------------------------------------------------------------

#### Enriched Specification per Ticket

For work in this repository with documented vertical slices on disk:

| Artifact | Location |
|-----------|-----------|
| Index and execution order | `.tasks/<PBI-or-other-id>/index-spec.md` |
| One story/slice per file | `.tasks/<id>/spec-<NN>-<kebab-name>.md` |
| Decision making | `.tasks/<id>/open-questions.md` |
| Solution diagrams | `.tasks/<id>/solution-diagrams.md` |

The official team template for the spec format is in **[templates/enriched-template.md](./templates/enriched-template.md)**.
The official template for solution diagrams is in **[templates/solution-diagrams.md](./templates/solution-diagrams.md)**.

##### `open-questions.md` Document — Mandatory Generation

**When to generate:** It is mandatory to generate the `open-questions.md` file during the decomposition and generation of specifications (`spec-*.md`) if blockers, ambiguities, or functional/technical inconsistencies are found. This is not an optional artifact: if there is at least one unresolved or debated item, the document must be created and completed immediately.

**Update rule:** Every time the user responds to an open decision in the document, reflect the change in the corresponding spec and mark the item as closed in the final summary.

The complete structure of the document, formatting rules, and a real-world example are in **[templates/open-questions.md](./templates/open-questions.md)**.

##### `solution-diagrams.md` Document — Mandatory Generation

**When to generate:** It is mandatory to generate the `solution-diagrams.md` file to capture the technical design and visual diagrams of the specified solution.

This file must be created immediately and include:
1. A **Sequence Diagram** detailing the flow of interactions and calls between components, actors, and systems.
2. A **Class Diagram** outlining the static structure, relationships, attributes, and methods of the solution.
3. A **Placeholder for an Additional Diagram** to help understand other aspects of the solution (e.g., state diagram, data flow, or component architecture).

The template and complete structure of this document are in **[templates/solution-diagrams.md](./templates/solution-diagrams.md)**.

--------------------------------------------------------------------------------

#### Project Context

| Aspect | Detail |
| ------ | ------ |
| Story Format | `As a [user role], I want [goal], so that [benefit]` |
| Acceptance Criteria | BDD format / Gherkin language (Given / When / Then) |
| Quality Framework | [INVEST Model](./invest-guidelines.md), SMART Criteria, Jobs-to-be-Done (JTBD) |
| Planning Approach | User Story Mapping (Jeff Patton), Outcomes > Output |

Relevant architecture for this skill:
Stories must represent functional vertical slices. In large projects and epics, the first slice must form a functional walking skeleton that runs end-to-end through the system to validate technical risk early.

--------------------------------------------------------------------------------

#### Critical Patterns

**A. Continuous Analysis and Empathy**

* **PATTERN 1: From 3Cs to 5Cs.** Ensure you don't get stuck in *Card, Conversation, Confirmation*; stories must plan for success by scaling to *Construction* and *Consequences*. Add metrics to know if the implemented feature actually delivered the desired benefit.
* **PATTERN 2: Prevention of the "Over-the-Wall" Antipatron.** Under no circumstances write and assume the isolated work of a Product Owner; force the user into a cycle of questions. Stories are constant invitations to converse.
* **PATTERN 3: Focus on User Personas and Jobs-to-be-Done (JTBD).** Abandon the use of the generic "user" role. Create and use detailed fictional archetypes that empathize with their demographics and motivations for the Role field. Focus on the fundamental job or problem the customer needs to solve (JTBD).
* **PATTERN 4: Shared Understanding over Documentation ("Talk and Doc").** The real goal of stories is not to write the perfect document, but to build a shared understanding through continuous conversations. Write to remember the conversation, not to replace it.

**B. Requirements Organization and Quality**

* **PATTERN 5: Strict Separation of Use Cases.** Do not allow the story to turn into a use case; focus on "what" the user needs and leave the "how" and system interactions for other documentations like diagrams.
* **PATTERN 6: Technical Stories and Spikes.** Write purely technical stories (such as infrastructure or refactoring) without forcing the "As a [role]" format. If there is high uncertainty, first generate a technical *Spike* to evaluate feasibility within a timeboxed exploration.
* **PATTERN 7: Separation of NFRs.** Never treat performance, scalability, accessibility, or security as simple acceptance criteria; isolate them as Non-Functional Requirements (NFRs) that impose systemic quality constraints.
* **PATTERN 8: Respect for the "Definition of Done" (DoD).** Acceptance criteria verify specific functional requirements; never include generic quality tasks (unit testing, code reviews) in them, as these belong to the project's mandatory DoD.
* **PATTERN 9: Plan-Validate-Execute for IA.** For complex requirements, first generate a structured plan or outline in a validation file, submit it for user approval, and then proceed with the final drafting in Gherkin.

**C. Writing Acceptance Criteria**

* **PATTERN 10: SMART Quality.** Design each criterion to be Specific, Measurable, Achievable, Relevant, and Time-bound. A good criterion is always verifiable in a binary way.
* **PATTERN 11: Universal BDD/Gherkin Language.** Strictly apply the base components: Given (context), When (triggering event), and Then (expected outcome).
* **PATTERN 12: Happy Flow First, Unhappy Flows Second.** Develop the main scenario assuming an ideal environment. Afterwards, intentionally break the scenario with errors or alternative paths.
* **PATTERN 13: Splitting Complex Criteria.** If a criterion chains too many conditions ("GIVEN a AND b WHEN c THEN d AND e"), you must split it into multiple individual criteria.
* **PATTERN 14: Three Amigos Rule.** Mentally simulate and guarantee that the criteria cover the alignment of three pillars: Business (PO), Development (IT), and Design/QA edge cases.

**D. Advanced Story Splitting (Vertical Slicing Strategies for Epics)**

* **PATTERN 15: Splitting by Workflow Steps (Strategy 1).** Split flows by isolating the start and end parts to create the MVP, deferring intermediate steps.
* **PATTERN 16: Splitting by Business Rules (Strategy 2).** Start by relaxing operational constraints and later incorporate hardening (legal rules, rejections) through subsequent stories.
* **PATTERN 17: Splitting by Input Options / Platforms (Strategy 4).** Generate separate stories based on the interface (App vs Web) or how data is entered.
* **PATTERN 18: Splitting by Data Types (Strategy 5).** Isolate requirements by extracting parameter complexity (e.g., simple search vs advanced filters).
* **PATTERN 19: Splitting by CRUD Operations (Strategy 6).** Penalize the use of the verb "Manage"; break it down into creation, reading, updating, and deletion.
* **PATTERN 20: Splitting by Test Scenarios (Strategy 7).** Use unhappy flows and complex edge cases to separate them from the parent requirement and create their own stories.
* **PATTERN 21: Splitting by Roles (Strategy 8).** Extract the goal into multiple stories if the result impacts ordinary customers, VIPs, or administrators in different ways.
* **PATTERN 22: Optimize Later (Strategy 9).** Apply "make it work first" leaving the base functionality and postpone severe performance improvements to future stories.
* **PATTERN 23: Technology Compatibility (Strategy 10).** Ensure value delivery by concentrating initial development on primary browsers or technologies.
* **PATTERN 24: "Good-Better-Best" Splitting.** To avoid paralysis, first define the "good enough for now" stories (Good), then extract those that would make the experience "Better" (Better), and leave the "Optimal" (Best) for last.

**E. User Story Mapping (Visual Product Planning)**

* **PATTERN 25: Outcomes over Output.** Your job is not to build more software, but to maximize the impact of the solution. Prioritize business outcomes before features.
* **PATTERN 26: Breadth before Depth (Mile Wide, Inch Deep).** When mapping, don't get lost in details. Build the "Backbone" first, grouping high-level activities in a left-to-right narrative flow before digging top-to-bottom.
* **PATTERN 27: Strategic Slicing (MVP).** Draw horizontal lines on the Story Map to slice away everything that isn't necessary, and group the stories of the first slice to form the functional MVP.
* **PATTERN 28: Functional Walking Skeleton.** In Slicing, do not split by technical layers. Create a first slice that is a functional end-to-end walking skeleton to discover technical risks immediately.

**F. Estimation and Economic Valuation Tools**

* **PATTERN 29: MoSCoW Matrix.** Provide context by helping the user label requirements into Must have, Should have, Could have, and Won't have.
* **PATTERN 30: Real Value Calculation (ROI / WSJF).** Apply WSJF prioritization (Cost of Delay / Size) encouraging measurements based on empirical economic benefits.

--------------------------------------------------------------------------------

#### Advanced Decision Tree

The agent must determine whether the request is a specific writing/refinement or a complete product mapping.

**FLOW 1: Analysis, Writing, and Splitting (Stories / Epics)**

1. **Does the user provide a requirement lacking an explicit Role, empirical Value, or "Why" context?**
   * YES: **Stop**. Ask questions to build a "User Persona" and use *Jobs-to-be-Done* to understand the need. Apply **Pattern 9**.
   * NO: Proceed to step 2.
2. **Is it a customer-facing requirement (functional) or a system technical requirement?**
   * TECHNICAL: Apply **Pattern 6** (Technical Story/Spike without "As a user" format).
   * FUNCTIONAL: Proceed to step 3.
3. **Does the request involve the ambiguous term "manage" or cover a giant flow (Epic)?**
   * YES: Evaluate applying division by **CRUD (Pattern 19)**, **Input Options (Pattern 17)**, or **Good-Better-Best (Pattern 24)**. Propose 2 or 3 splitting strategies.
   * NO: Proceed to step 4.
4. **Do the Acceptance Criteria (AC) only cover happy scenarios?**
   * YES: Interrupt. Apply **Pattern 12** requiring the definition of *unhappy flows*. If they are very risky, split them using **Pattern 20**.
   * NO: Proceed to step 5.
5. **Do the Acceptance Criteria drag in excessive validations or include requirements like "Load quickly"?**
   * YES: Refine and apply **Pattern 13** by splitting long criteria. Apply **Pattern 7 and 8** to separate Global Constraints (NFRs) and DoD.
   * NO: Proceed to structure in BDD/Gherkin syntax.
6. **During spec generation or refinement, were blockers, ambiguities, or inconsistencies detected?**
   * YES: **Mandatory generation of `open-questions.md`** detailing all points to resolve before implementing.
   * NO: Proceed to step 7.
7. **Mandatory generation of solution diagrams:**
   * **Mandatory generation of `solution-diagrams.md`** containing a sequence diagram of the solution flow, a class diagram of the technical design, and space for additional supporting diagrams to help illustrate development.
8. **Does the user know how to measure the impact after deployment?**
   * NO: Incorporate tracking metrics into the discussion (*Consequences* / Pattern 1).
   * YES: Generate the final agile user story.

**FLOW 2: User Story Mapping (Product Mapping / Visual Layout)**
If the user requests to "map", "create a flow", or "define an MVP":

1. **Frame the problem:** Has the user persona and expected outcome been defined (Outcome / Pattern 25)?
2. **Map the big picture (Backbone):** Define the backbone by chronologically ordering (left to right) the main activities (Pattern 26).
3. **Explore (Details):** Go deeper top-to-bottom. Ask for alternatives, business rules, or data variations.
4. **Slice out a release strategy (MVP):** Draw horizontal slicing lines focusing only on the minimum necessary to achieve the main outcome (Pattern 27).
5. **Slice out a learning strategy (Walking Skeleton):** If there is high technical risk, propose a "Functional Walking Skeleton" (Pattern 28) as the first slice (Slice 1).

--------------------------------------------------------------------------------

#### Examples

##### Example 1: Standard Gherkin Story (Happy/Unhappy Flow)

**Story:** As a customer, I want to withdraw cash from the ATM so that I can avoid queuing at the bank.
**Acceptance Criterion (Scenario 1: Happy flow)**:
* **Given** the account has credit and the card is valid
* **When** the customer requests cash
* **Then** the account is debited and the cash is dispensed.

**Acceptance Criterion (Scenario 2: Unhappy flow)**:
* **Given** the account exceeds the agreed overdraft limit
* **When** the customer requests cash
* **Then** the ATM shows a message denying the request.

##### Example 2: Story splitting by CRUD operations

*Request: "As a user, I want to manage my cart"*

* *Create:* As a shopper, I want to add new books to my cart to place the order.
* *Read:* As a shopper, I want to check the items in my cart to know the total.
* *Update:* As a shopper, I want to update the quantities of a book in my cart.

##### Example 3: User Story Mapping - Breadth (Backbone) vs Depth (Details)

**Backbone (Left to Right):** Search product -> Add to cart -> Pay -> Confirm shipment.
**Details under "Pay" (Top to Bottom):**
* *Good enough:* Pay with credit card (MVP).
* *Better:* Pay with PayPal.
* *Unhappy flow:* Show error if card is declined.

##### Example 4: Slicing and Functional Walking Skeleton

**Epic:** As an organizer, I want to manage event attendees.
* **Slice 1 (Walking Skeleton):** Manually register an attendee with name and email to verify the database flow works end-to-end.
* **Slice 2 (Make it better):** Import attendee list via CSV.
* **Slice 3 (Make it releasable):** Send automatic welcome email.

--------------------------------------------------------------------------------

#### Resources

* **Quality Guide**: [INVEST Guidelines and User Story Quality](./invest-guidelines.md)
* **Reference HTML Template**: [templates/user_story_template.md](./templates/user_story_template.md)
* **Solution Diagrams Template**: [templates/solution-diagrams.md](./templates/solution-diagrams.md)
* **Mapping Methodology**: [*User Story Mapping* by Jeff Patton (Concepts: Backbone, Narrative Flow, Outcomes > Output, Slicing)](./templates/key_concept_jeff_patton.md)
