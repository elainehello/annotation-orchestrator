```markdown
# 020 — Domain Model

**Document:** 020 — Domain Model
**Status:** Draft
**Version:** 0.1.0
**Last Updated:** 2026-07-02

---

## 1. Purpose

This document defines the domain concepts that build upon the primitive concepts 
from 010 — Ubiquitous Language.

For each concept, this document provides:
* A semantic definition
* Relationships to other concepts

This document does not define:
* Cardinality or constraints (030)
* Workflows or state transitions (040)
* Persistence or implementation patterns

---

## 2. Primitive Concepts

The primitive concepts Evidence, Claim, and Actor are defined in 
010 — Ubiquitous Language and are foundational to all concepts in this document.

---

## 3. Domain Concepts and Relationships

### Workspace

**Definition**

An administrative boundary for organizing collaborative work.

**Relationships**

```
Workspace ──organizes──> Project
Workspace ──organizes──> Dataset
Workspace ──organizes──> User
Workspace ──organizes──> Team
```

---

### Project

**Definition**

A coordinated body of work performed on Evidence.

**Relationships**

```
Project ──performed on──> Dataset
Project ──contains──> Task
User ──assigned to──> Task
```

---

### Dataset

**Definition**

An organized collection of Evidence.

**Relationships**

```
Dataset ──organized as──> Asset
Dataset ──organized as──> Scene
Project ──performed on──> Dataset
```

---

### Scene

**Definition**

A contextual grouping of Assets.

**Relationships**

```
Scene ──groups──> Asset
```

---

### Asset

**Definition**

A unit of Evidence.

**Relationships**

```
Asset ──instance of──> Evidence
Annotation ──about──> Asset
```

---

### Annotation

**Definition**

A Claim regarding Evidence.

**Relationships**

```
Annotation ──expresses──> Claim
Annotation ──about──> Asset
User ──creates──> Annotation
Task ──produces──> Annotation
```

---

### Task

**Definition**

A request for work.

**Relationships**

```
Task ──belongs to──> Project
Task ──produces──> Annotation
User ──assigned to──> Task
```

---

### User

**Definition**

An Actor in the context of this domain.

**Relationships**

```
User ──creates──> Annotation
User ──assigned to──> Task
User ──member of──> Team
```

---

### Team

**Definition**

A grouping of Users.

**Relationships**

```
Team ──contains──> User
Team ──part of──> Workspace
```

---

## 4. Semantic Constraints

**SC-005**

Incorrect

> An Annotation is owned by a Task.

Correct

> A Task produces an Annotation.

---

**SC-006**

Incorrect

> A Dataset is owned by a Project.

Correct

> A Project is performed on a Dataset.

---

**SC-007**

Incorrect

> A User belongs to a Project.

Correct

> A User is assigned to a Task that belongs to a Project.

---

**SC-008**

Incorrect

> An Asset contains an Annotation.

Correct

> An Annotation is about an Asset.

---

**SC-009**

Incorrect

> Evidence is organized into Datasets.

Correct

> Evidence is organized as Assets, which are organized into Datasets.

---

**SC-010**

Incorrect

> Claims are stored.

Correct

> Claims are created and preserve their history.

---

## Appendix A — Why These Concepts Exist

**Status:** Informative

### Why Workspace?

Collaborative work often occurs in separate, isolated contexts. Workspace 
provides a domain concept for administrative separation without prescribing 
implementation (multi-tenancy, permissions, billing, scoping, etc.).

### Why Project?

Evidence often requires organized coordination of work. Project provides a 
concept for grouping and choreographing that work without prescribing how it 
is organized (by task, by workflow, by team, etc.).

### Why Dataset?

Evidence requires organization for management, sharing, governance, and 
versioning. Dataset provides a concept for curated collections of Evidence 
without prescribing the organization scheme.

### Why Scene?

Evidence often contains contextual relationships. Scene provides a concept for 
grouping Evidence within a contextual boundary without prescribing what that 
context is (temporal, spatial, logical, domain-specific, etc.).

### Why Asset?

Evidence requires granular units for annotation and processing. Asset provides 
a concept for minimal observable units without prescribing modality, format, 
or structure.

### Why Annotation?

Claims require concrete expression in the domain of knowledge production. 
Annotation provides a concept for human-expressed Claims without prescribing 
encoding, format, or representation.

### Why Task?

Work requires coordination, assignment, and tracking. Task provides a concept 
for work requests without prescribing how work is organized, assigned, or 
executed.

### Why User?

Claims require attribution for accountability and provenance. User provides a 
concrete entity for that attribution in the context of this platform.

### Why Team?

Users often collaborate in groups. Team provides a concept for grouping Users 
for organization, permission, or analysis without prescribing team structure 
or semantics.

---

## Appendix B — Semantic Relationships Summary

**Status:** Informative

The following table summarizes all semantic relationships defined in this 
document.

```
Workspace ──organizes──> Project
Workspace ──organizes──> Dataset
Workspace ──organizes──> User
Workspace ──organizes──> Team

Project ──performed on──> Dataset
Project ──contains──> Task

Dataset ──organized as──> Asset
Dataset ──organized as──> Scene

Scene ──groups──> Asset

Asset ──instance of──> Evidence

Annotation ──expresses──> Claim
Annotation ──about──> Asset

Task ──belongs to──> Project
Task ──produces──> Annotation

User ──creates──> Annotation
User ──assigned to──> Task
User ──member of──> Team

Team ──contains──> User
Team ──part of──> Workspace
```

---

## Appendix C — Ubiquitous Language Reference

**Status:** Informative

The following terms are defined by this specification.

| Term | Definition |
|------|-----------|
| Annotation | A Claim regarding Evidence |
| Asset | A unit of Evidence |
| Dataset | An organized collection of Evidence |
| Project | A coordinated body of work performed on Evidence |
| Scene | A contextual grouping of Assets |
| Task | A request for work |
| Team | A grouping of Users |
| User | An Actor in the context of this domain |
| Workspace | An administrative boundary for organizing collaborative work |
```
