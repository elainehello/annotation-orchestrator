# 060 — Architecture

**Document:** 060 — Architecture
**Status:** Accepted
**Version:** 1.0.0
**Last Updated:** 2026-07-02

---

# 1. Purpose

This specification defines the architectural constraints that every
implementation shall satisfy.

Architecture explains how the preceding specifications are realized while
preserving their meaning.

This specification defines:

- architectural responsibilities
- dependency constraints
- traceability requirements
- conformance requirements

This specification does not define:

- software architecture styles
- programming languages
- frameworks
- persistence technologies
- communication protocols
- deployment topology
- implementation patterns

---

# 2. Relationship to Previous Specifications

The previous specifications define:

- what concepts exist (020)
- what must always be true (030)
- how concepts evolve (040)
- how concepts may be specialized (050)

Architecture defines how implementations preserve those specifications.

---

# 3. Architectural Principles

## AP-001 — Specification Authority

The specification is the authoritative definition of the domain.

Implementations realize the specification.

They do not redefine it.

---

## AP-002 — Semantic Preservation

Implementations shall preserve the semantic meaning established by the
specification.

Implementation details shall not alter domain meaning.

---

## AP-003 — Traceability

Every implementation element responsible for domain behavior shall be
traceable to one or more normative requirements defined in this
specification series.

---

## AP-004 — Separation of Concerns

Domain semantics shall remain independent from implementation technology.

Technology choices shall not modify domain meaning.

---

## AP-005 — Replaceability

Implementation technologies may be replaced without requiring changes to
the domain specification.

---

## AP-006 — Implementation Freedom

Any implementation approach is acceptable provided it satisfies this
specification.

Architecture is constrained by behavior, not by structure.

---

# 4. Architectural Responsibilities

Every implementation shall provide mechanisms that preserve:

- domain concepts
- domain relationships
- domain invariants
- workflow correctness
- capability conformance

How these mechanisms are organized is implementation-defined.

---

# 5. Dependency Constraints

Dependencies shall preserve semantic direction.

Implementations shall prevent implementation concerns from redefining domain
behavior.

Examples include:

- storage technology shall not define domain rules
- communication protocols shall not define workflows
- user interfaces shall not define invariants
- serialization shall not define semantics

The specification remains the source of truth.

---

# 6. Traceability

Implementations shall demonstrate traceability between:

| Specification | Implementation Responsibility |
|---------------|-------------------------------|
| 020 | Domain concepts |
| 030 | Invariant enforcement |
| 040 | Workflow realization |
| 050 | Capability specialization |

Traceability may be implemented using any suitable mechanism.

This specification does not prescribe how.

---

# 7. Conformance

An implementation conforms when:

1. every domain concept preserves its specified meaning;
2. every invariant is enforced;
3. every workflow preserves valid transitions;
4. every capability satisfies its requirements;
5. implementation technology does not redefine the domain.

---

# 8. Semantic Constraints

## SC-001

Incorrect

> The implementation defines the domain.

Correct

> The specification defines the domain.

---

## SC-002

Incorrect

> Storage technology determines domain behavior.

Correct

> Storage technology realizes domain behavior.

---

## SC-003

Incorrect

> Communication protocols determine workflow semantics.

Correct

> Workflows are defined by the specification.

---

## SC-004

Incorrect

> Architecture requires a particular design pattern.

Correct

> Any architectural style may conform if it satisfies this specification.

---

## SC-005

Incorrect

> Implementation structure determines correctness.

Correct

> Correctness is determined by conformance to the specification.

---

# Appendix A — Informative Examples

The following implementation styles can conform to this specification:

- layered architecture
- clean architecture
- hexagonal architecture
- onion architecture
- actor-based systems
- data-oriented architecture
- functional architecture
- service-oriented architecture

Conformance depends on preserving the specification rather than adopting a
particular architectural style.

---

# Appendix B — Informative Guidance

The architecture should make it straightforward to identify:

- where concepts are realized;
- where invariants are enforced;
- where workflows are implemented;
- where capabilities are specialized.

The organization of source code is intentionally left unspecified.

---

# Appendix C — Specification Boundary

This specification intentionally avoids prescribing:

- classes
- modules
- packages
- services
- repositories
- controllers
- dependency injection
- aggregates
- entities
- adapters
- ports
- interfaces

Those are implementation decisions.

Only conformance to the preceding specifications is normative.
