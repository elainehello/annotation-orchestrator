# 070 — Decisions

**Document:** 070 — Decisions
**Status:** Approved
**Version:** 1.0.0
**Last Updated:** 2026-07-02

---

# 1. Purpose

This document records the significant decisions that shaped this specification
series.

Each decision explains:

* what was decided
* why the decision was made
* alternatives that were considered
* consequences of the decision

This document is informative.

It explains the rationale behind the normative specifications contained in
000–060 but introduces no additional requirements.

---

# 2. Decision Format

Each decision contains:

* Decision
* Status
* Context
* Rationale
* Consequences
* Alternatives Considered

---

# 3. Decisions

---

## D-001 — Three Primitive Concepts

### Decision

Evidence, Claim, and Actor are the only primitive concepts in the ontology.

### Status

Stable

### Context

The ontology should remain minimal while still expressing every other concept
used throughout the specification.

### Rationale

Evidence represents observation.

Claim represents interpretation.

Actor represents attribution.

Every remaining concept can be expressed in terms of these three primitives.

Keeping the ontology minimal reduces conceptual complexity while maximizing
extensibility.

### Consequences

* The ontology remains stable.
* Future concepts derive from these primitives.
* Extensions preserve semantic consistency.

### Alternatives Considered

Introduce additional primitives such as Work, Validation, or Knowledge.

Rejected because each can be expressed using existing primitives.

---

## D-002 — Separate Knowledge from Work

### Decision

Tasks represent work.

Annotations represent knowledge.

These concepts have independent lifecycles.

### Status

Stable

### Context

Work management and knowledge production evolve differently over time.

Treating them as the same concept would couple operational history with domain
knowledge.

### Rationale

Tasks coordinate activity.

Annotations preserve Claims.

Separating them allows work records to evolve independently from durable
knowledge.

### Consequences

* Task lifecycle does not determine Annotation lifecycle.
* Knowledge survives operational changes.
* Correction workflows become straightforward.

### Alternatives Considered

Treat Tasks and Annotations as the same entity.

Rejected because operational state and knowledge state are fundamentally
different concerns.

---

## D-003 — Explicit Domain Workflows

### Decision

Core domain workflows are defined explicitly within this specification.

### Status

Stable

### Context

Implementations require a common behavioral model to preserve semantic
consistency.

### Rationale

Defining workflows for Tasks, Projects, and Annotations establishes consistent
state transitions while remaining independent of implementation technology.

The specification defines valid transitions.

Implementations determine how those transitions are enforced.

### Consequences

* Workflow behavior is consistent across implementations.
* State-machine implementations remain interchangeable.
* Workflow engines are optional implementation choices.

### Alternatives Considered

Leave workflows entirely implementation-defined.

Rejected because identical concepts could otherwise evolve differently across
implementations.

---

## D-004 — Capabilities Extend Rather Than Modify

### Decision

Capabilities extend existing domain concepts without modifying the core model.

### Status

Stable

### Context

Different domains require different specializations.

### Rationale

Capabilities provide realization-specific behavior while preserving the
underlying semantic concepts.

The core model remains stable as new capabilities emerge.

### Consequences

* Unlimited specialization is possible.
* Core specifications remain unchanged.
* Domain semantics remain consistent.

### Alternatives Considered

Embed every specialization directly into the domain model.

Rejected because the core model would continuously expand.

---

## D-005 — Specification Before Implementation

### Decision

The specification is authoritative.

Implementations realize the specification.

### Status

Stable

### Context

Without an authoritative specification, implementations gradually diverge.

### Rationale

The specification defines meaning.

Implementations preserve that meaning.

Traceability ensures implementation remains aligned with specification.

### Consequences

* Architectural drift is reduced.
* Domain terminology remains consistent.
* Conformance can be evaluated objectively.

### Alternatives Considered

Allow implementation to become the primary source of truth.

Rejected because semantic consistency would gradually erode.

---

## D-006 — Domain Before Technology

### Decision

Technology choices are implementation decisions.

Domain concepts are specification decisions.

### Status

Stable

### Context

Programming languages, databases, frameworks, and deployment models evolve
more rapidly than domain semantics.

### Rationale

Separating semantic requirements from implementation technology allows the
specification to remain stable across technological change.

### Consequences

* Multiple architectures may conform.
* Technology migrations do not affect the specification.
* Domain semantics remain stable.

### Alternatives Considered

Recommend specific architectural patterns or technologies.

Rejected because such guidance becomes obsolete over time.

---

## D-007 — Domain Concepts Describe Meaning

### Decision

The domain model defines concepts by semantic meaning rather than by software
structure.

### Status

Stable

### Context

Concepts should exist because they represent real distinctions within the
domain, not because they simplify implementation.

### Rationale

Separating semantics from implementation enables multiple architectural
realizations without changing the domain language.

### Consequences

* Domain terminology remains implementation-independent.
* Different software designs can represent the same semantics.
* Specifications remain technology-neutral.

### Alternatives Considered

Define concepts according to implementation patterns.

Rejected because implementation techniques evolve more rapidly than domain
semantics.

---

## D-008 — Invariants Preserve Semantic Integrity

### Decision

Invariants define rules that preserve semantic consistency across every
implementation.

### Status

Stable

### Context

Implementations may differ internally while representing the same domain.

### Rationale

Invariant enforcement guarantees that different implementations preserve the
same domain meaning.

### Consequences

* Conformance becomes testable.
* Implementations remain interoperable at the semantic level.
* Domain rules remain independent of technology.

### Alternatives Considered

Treat invariants as implementation guidance.

Rejected because core semantics would no longer be guaranteed.

---

## D-009 — Layered Responsibilities

### Decision

Architecture separates domain logic, application logic, infrastructure, and
interfaces according to responsibility.

### Status

Stable

### Context

Mixing concerns reduces maintainability and obscures domain meaning.

### Rationale

Each layer has a distinct purpose.

Separating responsibilities improves traceability and preserves domain
integrity.

### Consequences

* Domain logic remains technology-independent.
* Infrastructure can evolve independently.
* Interfaces remain replaceable.

### Alternatives Considered

Allow unrestricted dependencies between architectural concerns.

Rejected because domain semantics become coupled to implementation.

---

## D-010 — Evolution Through Specification

### Decision

The specification evolves through amendments rather than implementation
exceptions.

### Status

Stable

### Context

New requirements inevitably emerge.

### Rationale

Updating the specification first preserves consistency across every conforming
implementation.

### Consequences

* Evolution remains controlled.
* Conformance remains measurable.
* Implementations evolve together.

### Alternatives Considered

Allow implementations to introduce undocumented concepts.

Rejected because specifications would eventually lose authority.

---

# 4. Decisions Under Review

None.

---

# 5. Deprecated Decisions

None.

---

# Appendix A — Design Philosophy

**Status:** Informative

The specification series is guided by four principles.

## Specification First

Meaning is defined before implementation.

---

## Minimal Ontology

Only irreducible concepts belong in the ontology.

---

## Stable Semantics

Semantic meaning evolves slowly.

Implementation evolves rapidly.

---

## Implementation Independence

The specification defines what must be preserved.

Implementations determine how preservation is achieved.

---

# Appendix B — Relationship to the Specification Series

**Status:** Informative

The documents build upon one another.

```
000  Vision
        ↓
010  Ubiquitous Language
        ↓
020  Domain Model
        ↓
030  Invariants
        ↓
040  Workflows
        ↓
050  Capabilities
        ↓
060  Architecture
        ↓
070  Decisions
```

070 records why the preceding documents were designed as they were.

It introduces no additional normative requirements.
