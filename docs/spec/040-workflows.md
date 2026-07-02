# 040 — Workflows

**Document:** 040 — Workflows
**Status:** Accepted
**Version:** 1.0.0
**Last Updated:** 2026-07-02

---

# 1. Purpose

This specification defines the workflow model governing the progression of work
within the domain.

A workflow describes how work progresses through a sequence of states by means
of transitions.

This specification defines the semantic concepts of workflows without
prescribing any particular workflow.

It does not define:

- workflow templates;
- state names;
- implementation mechanisms;
- authorization rules; or
- user interaction.

---

# 2. Workflow Concepts

## Workflow

A workflow defines the valid progression of work.

---

## State

A state represents a recognizable condition within a workflow.

---

## Transition

A transition represents movement from one state to another.

---

## Initial State

Every workflow has an initial state.

---

## Terminal State

A workflow may define one or more terminal states.

A terminal state has no outgoing transitions.

---

# 3. Workflow Invariants

## W-001

Every workflow contains at least one state.

---

## W-002

Every workflow contains exactly one initial state.

---

## W-003

Every transition connects two states belonging to the same workflow.

---

## W-004

Every transition has exactly one source state.

---

## W-005

Every transition has exactly one destination state.

---

## W-006

Every state is reachable from the initial state.

---

## W-007

Every terminal state is reachable through one or more transitions.

---

## W-008

A transition does not alter the identity of the work progressing through the
workflow.

Transitions change state, not identity.

---

## W-009

Workflow progression preserves the invariants defined in
030 — Invariants.

---

# 4. Semantic Constraints

## SC-001

Incorrect

> A workflow may contain transitions without states.

Correct

> Every transition connects two states.

---

## SC-002

Incorrect

> A workflow may have multiple initial states.

Correct

> Every workflow has exactly one initial state.

---

## SC-003

Incorrect

> A transition may connect different workflows.

Correct

> A transition connects states within the same workflow.

---

## SC-004

Incorrect

> A transition creates new work.

Correct

> A transition changes the state of existing work.

---

## SC-005

Incorrect

> Workflow execution may violate domain invariants.

Correct

> Workflow progression preserves all domain invariants.

---

## Appendix A — Rationale

**Informative**

Workflows describe progression rather than meaning.

The meaning of domain concepts is established by the ontology, domain model,
and invariants.

Workflows define only how work progresses through recognizable states.

Keeping workflows abstract allows different domains to define different state
models while remaining conformant to the same specification.

---

## Appendix B — Rejected Constraints

**Informative**

### Finding

Specific workflow states are not normative.

### Reasoning

Different domains require different workflow vocabularies.

---

### Finding

Review, approval, and archival are not universal workflow stages.

### Reasoning

Some workflows require them; others do not.

---

### Finding

Workflow templates are not specified.

### Reasoning

Template definition is a capability rather than a semantic property of the
domain.
