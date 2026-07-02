# 050 — Capabilities

**Document:** 050 — Capabilities
**Status:** Accepted
**Version:** 1.0.0
**Last Updated:** 2026-07-02

---

# 1. Purpose

This specification defines how the domain may be extended without changing the
foundational concepts established by previous specifications.

A capability defines an optional specialization of one or more existing domain
concepts.

This specification defines:

- what constitutes a capability
- the requirements every capability must satisfy
- how capabilities extend the domain
- the invariants governing capability design

This specification does not define:

- specific capabilities
- implementation mechanisms
- software architecture
- persistence
- communication protocols
- encoding formats

---

# 2. Relationship to Previous Specifications

The preceding specifications establish the stable foundation of the domain.

- 010 defines primitive concepts.
- 020 defines domain concepts.
- 030 defines invariants.
- 040 defines workflows.

Capabilities extend those specifications without modifying them.

---

# 3. Capability

## Definition

A capability is an optional specialization of an existing domain concept.

A capability adds domain-specific meaning while preserving the identity,
relationships, invariants, and workflows of the concept it specializes.

Capabilities extend the domain.
They do not redefine it.

---

# 4. Capability Requirements

## C-001

Every capability specializes at least one concept defined by this
specification series.

Capabilities shall not introduce independent foundational concepts.

---

## C-002

A capability preserves the semantic meaning of every concept it
specializes.

Specialization adds meaning.
It does not replace existing meaning.

---

## C-003

Every capability conforms to all applicable invariants defined in
030 — Invariants.

No capability may weaken or contradict a domain invariant.

---

## C-004

Every capability conforms to all applicable workflows defined in
040 — Workflows.

Capabilities may specialize behavior but shall not invalidate workflow
semantics.

---

## C-005

Capabilities are independent.

The existence or removal of one capability shall not alter the semantic
correctness of another capability.

---

## C-006

Capabilities are optional.

The domain model remains complete without any particular capability.

---

## C-007

A capability shall not require modification of any concept defined by
010, 020, 030, or 040.

If modification is required, the extension is not a capability.

It is a revision of the domain specification.

---

## C-008

Capabilities may define additional constraints.

Additional constraints may strengthen specialization.

They shall never weaken existing domain invariants.

---

# 5. Capability Structure

A capability may define:

- specialized vocabulary
- additional constraints
- additional states
- additional relationships
- additional domain rules

All additions shall remain consistent with previous specifications.

---

# 6. Conformance

A capability conforms to this specification when:

1. it specializes existing concepts;
2. it preserves existing semantics;
3. it satisfies every applicable invariant;
4. it satisfies every applicable workflow;
5. it does not contradict previous specifications.

---

# 7. Extending the Domain

A proposed extension is evaluated in the following order.

---

## Step 1

Does it introduce a new foundational concept?

If yes,
the change belongs in 020.

---

## Step 2

Does it introduce a new invariant?

If yes,
the change belongs in 030.

---

## Step 3

Does it introduce a new lifecycle?

If yes,
the change belongs in 040.

---

## Step 4

Does it merely specialize an existing concept?

If yes,
it is a capability.

---

# 8. Semantic Constraints

## SC-001

Incorrect

> A capability defines a new domain concept.

Correct

> A capability specializes an existing domain concept.

---

## SC-002

Incorrect

> A capability may contradict an invariant.

Correct

> Every capability satisfies all applicable invariants.

---

## SC-003

Incorrect

> A capability changes the meaning of Annotation.

Correct

> A capability specializes Annotation while preserving its meaning.

---

## SC-004

Incorrect

> Removing a capability changes the domain model.

Correct

> Removing a capability removes only that specialization.

---

## SC-005

Incorrect

> A capability extends the ontology.

Correct

> Capabilities extend the domain model while preserving the ontology.

---

# Appendix A — Rationale

**Status:** Informative

The previous specifications establish what exists, what must always be true,
and how concepts evolve.

Capabilities allow domains to introduce specialized meaning without modifying
those foundational specifications.

For example, different domains may specialize Annotation in different ways.

Those specializations remain Annotations.

Likewise, different domains may specialize Assets differently.

Those specializations remain Assets.

The capability mechanism therefore supports unlimited specialization while
preserving semantic consistency across the platform.

---

# Appendix B — Examples

**Status:** Informative

Examples of possible capabilities include:

- image annotation
- point-cloud annotation
- semantic segmentation
- medical contour annotation
- temporal event annotation

These examples are illustrative only.

They are not part of the normative specification.

---

# Appendix C — Specification Boundary

**Status:** Informative

Capabilities describe domain specialization.

They do not prescribe:

- software plugins
- modules
- packages
- interfaces
- serialization
- validation algorithms
- storage formats
- communication protocols

Those concerns belong to implementation.
