# 010 — Ubiquitous Language

**Document:** 010 — Ubiquitous Language
**Status:** Accepted
**Version:** 0.3.0
**Last Updated:** 2026-07-02

---

# 1. Purpose

This document establishes the irreducible concepts of the problem domain and
the vocabulary used consistently throughout this specification.

It defines:

- the ontological method used to identify primitive concepts;
- the primitive concepts themselves;
- the primitive relationships between those concepts; and
- the vocabulary established by this specification.

This document does not define:

- domain entities;
- aggregate boundaries;
- workflows or processes;
- invariants;
- persistence models;
- implementation technologies.

---

# 2. Ontological Method

A concept is **primitive** if it cannot be expressed in terms of other domain
concepts without loss of meaning.

A concept is **derived** if it can be expressed as a specialization,
combination, or property of primitive concepts.

Primitive concepts are identified by applying the following method.

A candidate concept SHALL satisfy all of the following:

1. It describes the problem domain independently of this platform.
2. It cannot be reduced to existing domain concepts.
3. Removing the concept would make the domain incomplete.

Applying this method yields the primitive concepts defined by this document.

---

# 3. Primitive Concepts

## Evidence

**Definition**

Information about the world.

---

## Claim

**Definition**

An assertion regarding Evidence.

---

## Actor

**Definition**

An entity to which Claims may be attributed.

---

# 4. Primitive Relationships

The following relationships define the ontological structure of the domain.

---

### R-001

Claims refer to Evidence.

```
Claim ─────────► Evidence
```

---

### R-002

Claims originate from Actors.

```
Claim ◄──────── Actor
```

---

### R-003

Evidence exists independently of Claims.

```
Evidence ─────► Claim
(independent)
```

Subsequent specifications may introduce additional concepts and relationships,
provided they do not contradict those defined here.

---

# 5. Ubiquitous Language

The following terms are defined by this specification.

---

## Actor

An entity to which Claims may be attributed.

---

## Claim

An assertion regarding Evidence.

---

## Evidence

Information about the world.

---

## Provenance

Information describing the origin and derivation of a Claim.

---

The following terms are reserved by this specification and are defined in
subsequent documents.

- Annotation
- Asset
- Dataset
- Project
- Scene
- Task
- Workflow
- Workspace

The term **Trusted Knowledge** is defined by **000 — Vision**.

---

# 6. Semantic Constraints

The following interpretations are prohibited.

---

### SC-001

Incorrect

> Evidence is something that is annotated.

Correct

> Claims are made regarding Evidence.

---

### SC-002

Incorrect

> Claims own Evidence.

Correct

> Claims refer to Evidence.

---

### SC-003

Incorrect

> Claims may be removed without preserving their history.

Correct

> The history of Claims MUST be preserved.

---

### SC-004

Incorrect

> Organizational structures define the ontology.

Correct

> Organizational structures are introduced by later specifications.

---

# Appendix A — Ontological Foundations

**Status:** Informative

## Why Evidence is Primitive

Evidence exists independently of interpretation.

Removing Evidence leaves Claims without subject matter.

Evidence therefore satisfies the ontological method.

---

## Why Claim is Primitive

Claims introduce assertions regarding Evidence.

Removing Claims leaves the domain unable to represent interpretation.

Claims therefore satisfy the ontological method.

---

## Why Actor is Primitive

Claims require attribution.

Removing Actors eliminates provenance and accountability.

Actors therefore satisfy the ontological method.

---

## Why These Relationships

The ontology establishes three primitive relationships.

- Claims refer to Evidence.
- Claims originate from Actors.
- Evidence exists independently of Claims.

Subsequent specifications extend this ontology without contradicting these
relationships.

---

# Appendix B — Investigated Concepts

**Status:** Informative

This appendix records concepts investigated during development of the ontology
that were determined not to be primitive.

Recording rejected concepts documents the application of the ontological method
and provides guidance for future revisions.

---

## Work

**Finding**

Not primitive.

**Reasoning**

Work can be expressed through relationships among primitive concepts.
Removing Work does not make the ontology incomplete.

---

## Validation

**Finding**

Not primitive.

**Reasoning**

Validation is activity applied to Claims rather than an irreducible concept.

---

## Trusted Knowledge

**Finding**

Not primitive.

**Reasoning**

Trusted Knowledge is an objective of the platform and an epistemic state of
Claims, not an ontological primitive.

---

## Revision

**Finding**

Not primitive.

**Reasoning**

The ontology requires preservation of Claim history but does not prescribe how
history is represented.

---

## Annotation

**Finding**

Not primitive.

**Reasoning**

Annotation is a domain realization defined by the domain model rather than an
irreducible concept.

---

## Dataset

**Finding**

Not primitive.

**Reasoning**

Dataset is an organizational concept applied to Evidence.

---

## Scene

**Finding**

Not primitive.

**Reasoning**

Scene is a domain concept introduced by the domain model.

---

## Asset

**Finding**

Not primitive.

**Reasoning**

Asset is a domain concept introduced by the domain model.

---

## Workspace

**Finding**

Not primitive.

**Reasoning**

Workspace is an organizational construct rather than an ontological concept.

---

## Project

**Finding**

Not primitive.

**Reasoning**

Project is an organizational construct rather than an ontological concept.
