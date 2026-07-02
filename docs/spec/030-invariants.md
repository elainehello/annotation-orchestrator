# 030 — Invariants

**Document:** 030 — Invariants
**Status:** Accepted
**Version:** 1.0.0
**Last Updated:** 2026-07-02

---

# 1. Purpose

This specification defines the invariants governing the domain concepts introduced
by 020 — Domain Model.

An invariant is a condition that MUST remain true regardless of workflow,
implementation, or technology.

This specification establishes:

- semantic dependencies;
- preservation requirements; and
- domain constraints.

This specification does not define:

- workflows;
- state transitions;
- implementation strategies;
- persistence mechanisms; or
- application architecture.

---

# 2. Method

A rule qualifies as an invariant only if violating it would change the meaning
of the domain.

Implementation convenience, architectural preference, and optimization are not
sufficient justification for a normative invariant.

---

# 3. Evidence

## I-001

Evidence exists independently of Claims.

The existence, modification, or removal of a Claim does not alter the existence
of the Evidence to which it refers.

---

## I-002

Evidence may be the subject of multiple Claims.

---

# 4. Claims

## I-003

Every Claim refers to Evidence.

---

## I-004

Every Claim is attributable to an Actor.

A Claim cannot exist without attribution.

---

## I-005

The provenance of every Claim MUST be preserved.

---

## I-006

The history of every Claim MUST be preserved.

Modification of a Claim does not eliminate its previous states.

---

# 5. Actors

## I-007

An Actor may produce multiple Claims.

---

## I-008

A Claim has exactly one originating Actor.

---

# 6. Domain Concepts

## I-009

An Annotation expresses a Claim.

---

## I-010

An Asset is Evidence.

---

## I-011

A User is an Actor.

---

# 7. Preservation

## I-012

Knowledge derived from Evidence MUST remain reproducible from its preserved
history and provenance.

---

# 8. Semantic Constraints

## SC-001

Incorrect

> Claims create Evidence.

Correct

> Claims refer to Evidence.

---

## SC-002

Incorrect

> Evidence depends upon Claims.

Correct

> Claims depend upon Evidence.

---

## SC-003

Incorrect

> Claims may exist without attribution.

Correct

> Every Claim is attributable to an Actor.

---

## SC-004

Incorrect

> Updating a Claim replaces its previous state.

Correct

> The previous state of a Claim is preserved.

---

## SC-005

Incorrect

> Provenance may be discarded after validation.

Correct

> Provenance is preserved for the lifetime of the Claim.

---

## Appendix A — Rationale

**Informative**

Evidence represents observations of the world.

Claims represent interpretations of Evidence.

Actors provide attribution for Claims.

These dependencies establish the minimum semantic structure necessary for the
production of trusted knowledge.

Preservation of provenance and history ensures that knowledge remains
reproducible, explainable, and auditable throughout its lifetime.

---

## Appendix B — Rejected Invariants

**Informative**

### Finding

Cardinality between Projects, Datasets, Tasks, Workspaces, Teams, Scenes, and
Assets is not established by the ontology.

### Reasoning

Those relationships describe one possible realization of the domain rather than
a universal semantic truth.

---

### Finding

Ownership relationships are not invariants.

### Reasoning

Ownership is an implementation decision rather than a property of the domain.

---

### Finding

Aggregate boundaries are not invariants.

### Reasoning

Consistency boundaries belong to software architecture rather than domain
semantics.
