# 100 — Domain Objects

**Document:** 100 — Domain Objects
**Status:** Approved
**Version:** 1.0.0
**Last Updated:** 2026-07-02
**Type:** Implementation Design

---

# 1. Purpose

This document defines how the domain concepts specified in **020 — Domain
Model** are realized as software objects in this implementation.

These design decisions apply only to this implementation. They are not part of
the normative specification and do not constrain other conforming
implementations.

This document defines:

- The primary domain objects
- The responsibility of each object
- Relationships between objects
- Aggregate boundaries for consistency
- Traceability to the specification

This document does not define:

- Programming language constructs
- Public APIs
- Persistence mechanisms
- Serialization formats
- Frameworks
- Repository implementations

---

# 2. Design Principles

Every domain object shall:

- Realize exactly one domain concept from the specification
- Encapsulate a single responsibility
- Enforce applicable domain invariants
- Preserve workflow semantics
- Expose only domain-meaningful behavior
- Be independently testable
- Remain independent of infrastructure concerns

Objects represent domain concepts—not storage structures, transport formats,
or user interface models.

---

# 3. Traceability

| Domain Object | Realizes Specification Concept |
|---------------|--------------------------------|
| Workspace | 020 — Workspace |
| Project | 020 — Project |
| Dataset | 020 — Dataset |
| Scene | 020 — Scene |
| Asset | 020 — Asset |
| Annotation | 020 — Annotation |
| Task | 020 — Task |
| User | 020 — User |
| Team | 020 — Team |

Every domain object is directly traceable to exactly one concept defined in
020 — Domain Model.

---

# 4. Object Responsibility Matrix

| Object | Primary Responsibility | References | Enforces |
|---------|-----------------------|------------|----------|
| Workspace | Administrative boundary | Projects, Datasets, Users, Teams | Workspace invariants |
| Project | Coordinate work | Datasets, Tasks | Project invariants |
| Dataset | Organize Evidence | Assets, Scenes | Dataset invariants |
| Scene | Contextually group Assets | Assets | Scene invariants |
| Asset | Represent Evidence | Dataset | Evidence invariants |
| Annotation | Express a Claim | Assets, User | Claim invariants |
| Task | Coordinate work | Project, Annotation | Task workflow |
| User | Represent an Actor | Workspace, Teams | Attribution invariants |
| Team | Organize Users | Users | Team invariants |

---

# 5. Domain Objects

## 5.1 Asset

**Realizes**

Asset (020)

**Responsibility**

Represent a single unit of Evidence.

**Enforces**

Applicable Evidence invariants defined in 030.

**Relationships**

- Belongs to one Dataset
- May belong to a Scene
- May be referenced by multiple Annotations

**Notes**

Asset represents immutable Evidence.

Changes in interpretation are expressed through new or updated Claims, never by
modifying the Asset itself.

---

## 5.2 Scene

**Realizes**

Scene (020)

**Responsibility**

Provide contextual grouping for related Assets.

**Enforces**

Scene invariants defined in 030.

**Relationships**

- Belongs to one Dataset
- Groups one or more Assets

**Notes**

Scene provides organization only.

It does not own Assets.

---

## 5.3 Dataset

**Realizes**

Dataset (020)

**Responsibility**

Organize and manage collections of Evidence.

**Enforces**

Dataset invariants defined in 030.

**Relationships**

- Contains Assets
- May organize Assets into Scenes
- May participate in multiple Projects
- Belongs to one Workspace

---

## 5.4 Annotation

**Realizes**

Annotation (020)

**Responsibility**

Express a Claim regarding one or more Assets.

**Enforces**

Claim invariants defined in 030.

Workflow transitions follow 040.

**Relationships**

- References one or more Assets
- Created by one User
- Produced through a Task

**Notes**

Annotation preserves its complete history.

The mechanism used to preserve history is an implementation decision and is
outside the scope of this document.

---

## 5.5 Task

**Realizes**

Task (020)

**Responsibility**

Coordinate a unit of work.

**Enforces**

Task invariants from 030.

Workflow transitions defined in 040.

**Relationships**

- Belongs to one Project
- Produces Annotations
- Assigned to one or more Users

**Notes**

Task is operational.

It coordinates work but does not own the knowledge produced.

---

## 5.6 User

**Realizes**

User (020)

**Responsibility**

Represent an Actor capable of producing Claims.

**Enforces**

Attribution invariants.

**Relationships**

- Belongs to one Workspace
- May belong to multiple Teams
- Creates Annotations
- May participate in multiple Tasks

---

## 5.7 Team

**Realizes**

Team (020)

**Responsibility**

Organize Users for collaboration.

**Enforces**

Team invariants.

**Relationships**

- Belongs to one Workspace
- Contains Users

**Notes**

Team membership is organizational.

It does not change domain semantics.

---

## 5.8 Project

**Realizes**

Project (020)

**Responsibility**

Coordinate work performed on Datasets.

**Enforces**

Project invariants.

Workflow progression follows 040.

**Relationships**

- Belongs to one Workspace
- References one or more Datasets
- Coordinates multiple Tasks

---

## 5.9 Workspace

**Realizes**

Workspace (020)

**Responsibility**

Provide the administrative boundary for this implementation.

**Enforces**

Workspace invariants.

**Relationships**

- Contains Projects
- Contains Datasets
- Contains Users
- Contains Teams

---

# 6. Relationships

| Source | Relationship | Target |
|----------|--------------|--------|
| Workspace | contains | Project |
| Workspace | contains | Dataset |
| Workspace | contains | User |
| Workspace | contains | Team |
| Project | coordinates | Task |
| Project | references | Dataset |
| Dataset | contains | Asset |
| Dataset | organizes | Scene |
| Scene | groups | Asset |
| Task | produces | Annotation |
| Annotation | references | Asset |
| User | creates | Annotation |
| Team | contains | User |

These relationships realize the semantic relationships defined by the
specification.

---

# 7. Aggregate Boundaries

This implementation defines the following aggregate roots.

| Aggregate Root | Protects |
|----------------|----------|
| Workspace | Administrative consistency |
| Project | Project coordination |
| Dataset | Evidence organization |
| Task | Workflow progression |
| Annotation | Claim consistency |

Aggregate boundaries are implementation decisions and are not part of the
normative specification.

---

# 8. Design Decisions

## D-100-001

Each domain object realizes exactly one specification concept.

This preserves one-to-one traceability between specification and
implementation.

---

## D-100-002

History preservation is required.

The implementation mechanism used to preserve history is intentionally left
unspecified.

---

## D-100-003

Assets are immutable.

Interpretation changes occur through Claims rather than modification of
Evidence.

---

## D-100-004

Tasks coordinate work.

Annotations preserve knowledge.

Operational work and durable knowledge remain separate concerns.

---

# Appendix A — Relationship to the Specification

This document realizes:

- 020 — Domain Model
- 030 — Invariants
- 040 — Workflows
- 050 — Capabilities
- 060 — Architecture

No new domain concepts are introduced.

---

# Appendix B — Related Design Documents

The implementation design continues with:

- 110 — Value Objects
- 120 — Domain Events
- 130 — Domain Services
- 140 — Aggregates
- 150 — Repositories
- 160 — Factories
- 170 — Policies

Together these documents define how this implementation realizes the semantic
contract established by the specification.
