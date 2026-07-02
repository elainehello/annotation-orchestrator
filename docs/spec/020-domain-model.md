# 020 — Domain Model

**Document:** 020 — Domain Model  
**Status:** Accepted  
**Version:** 1.0.0  
**Last Updated:** 2026-07-02

---

# 1. Purpose

This document defines the domain concepts that build upon the ontology
established in **010 — Ubiquitous Language**.

For each concept, this specification defines:

- its semantic meaning
- its semantic relationships to other concepts

This document does not define:

- invariants or cardinality (030)
- workflows or state transitions (040)
- implementation or architectural patterns
- persistence or storage technologies

---

# 2. Primitive Concepts

The primitive concepts **Evidence**, **Claim**, and **Actor** are defined by
**010 — Ubiquitous Language** and are referenced throughout this document.

---

# 3. Domain Concepts

## Workspace

**Definition**

An administrative boundary for organizing collaborative work.

**Relationships**

```
Workspace
    organizes
        Project
        Dataset
        User
        Team
```

---

## Project

**Definition**

A coordinated body of work performed on Evidence.

**Relationships**

```
Project
    performed on
        Dataset
```

---

## Dataset

**Definition**

An organized collection of Evidence.

**Relationships**

```
Dataset
    organized as
        Asset

Dataset
    may include
        Scene
```

---

## Scene

**Definition**

A contextual grouping of Evidence.

**Relationships**

```
Scene
    groups
        Asset
```

---

## Asset

**Definition**

A unit of Evidence.

**Relationships**

```
Annotation
    about
        Asset
```

---

## Annotation

**Definition**

A Claim regarding Evidence.

**Relationships**

```
Annotation
    about
        Asset

User
    creates
        Annotation

Task
    produces
        Annotation
```

---

## Task

**Definition**

A request for work.

**Relationships**

```
Task
    produces
        Annotation
```

---

## User

**Definition**

An Actor within this domain.

**Relationships**

```
User
    creates
        Annotation
```

---

## Team

**Definition**

A grouping of Users.

---

# 4. Semantic Constraints

**SC-001**

Incorrect

> An Annotation contains Evidence.

Correct

> An Annotation is a Claim about Evidence.

---

**SC-002**

Incorrect

> An Asset contains Annotations.

Correct

> Annotations are about Assets.

---

**SC-003**

Incorrect

> A Project owns a Dataset.

Correct

> A Project is performed on a Dataset.

---

**SC-004**

Incorrect

> A Task owns an Annotation.

Correct

> A Task produces an Annotation.

---

**SC-005**

Incorrect

> A User is a Claim.

Correct

> A User creates Claims through Annotations.

---

# Appendix A — Domain Concept Rationale

**Status:** Informative

## Workspace

Provides a domain concept for administrative separation of collaborative work.

---

## Project

Provides a domain concept for coordinating work performed on Evidence.

---

## Dataset

Provides a domain concept for organizing Evidence.

---

## Scene

Provides a domain concept for contextual organization of Evidence.

---

## Asset

Provides a domain concept representing a unit of Evidence.

---

## Annotation

Provides a domain concept representing the expression of a Claim regarding Evidence.

---

## Task

Provides a domain concept representing requested work.

---

## User

Provides a domain concept representing an Actor participating in the platform.

---

## Team

Provides a domain concept representing collaborative groups of Users.
