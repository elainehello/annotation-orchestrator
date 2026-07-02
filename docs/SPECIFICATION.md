# Annotation Orchestrator Specification

**Status:** Active
**Version:** 1.0.0
**Last Updated:** 2026-07-02

---

# Purpose

This repository contains the normative specification for Annotation
Orchestrator.

The specification defines the platform independently of any programming
language, framework, storage technology, or implementation.

Implementations conform to this specification.
The specification does not conform to implementations.

---

# Specification Structure

The specification is organized as a sequence of documents.

Each document answers exactly one question and depends only on documents
that precede it.

| ID | Document | Question | Status | Version |
|----|----------|----------|--------|---------|
| 000 | Vision | Why does the platform exist? | Accepted | 1.0.0 |
| 010 | Ubiquitous Language | What concepts exist? | Accepted | 1.0.0 |
| 020 | Domain Model | How are concepts realized? | Draft | 0.1.0 |
| 030 | Invariants | What must always be true? | Planned | — |
| 040 | Workflows | How do concepts evolve? | Planned | — |
| 050 | Capabilities | How is the platform extended? | Planned | — |

---

# Document Dependencies

Documents depend only on earlier documents.

```
000 Vision
      │
      ▼
010 Ubiquitous Language
      │
      ▼
020 Domain Model
      │
      ▼
030 Invariants
      │
      ▼
040 Workflows
      │
      ▼
050 Capabilities
```

A document MAY reference any preceding document.

A document MUST NOT contradict any preceding document.

---

# Document Lifecycle

Each specification document progresses through the following states.

| Status | Meaning |
|---------|---------|
| Draft | Under active development. Breaking changes are expected. |
| Review | Submitted for technical review. |
| Accepted | Normative and part of the specification baseline. |
| Superseded | Replaced by a newer version. |

---

# Versioning

Each document is versioned independently.

Semantic Versioning is used.

| Change | Version |
|----------|----------|
| Editorial correction | PATCH |
| Clarification without changing meaning | MINOR |
| Normative change | MAJOR |

Examples:

- 1.0.0 → Initial accepted document
- 1.0.1 → Editorial corrections
- 1.1.0 → Clarification
- 2.0.0 → Normative revision

---

# Conformance

An implementation conforms to this specification if it satisfies every
normative requirement of every Accepted document it claims to implement.

Informative appendices provide rationale and examples.

They do not introduce normative requirements.

---

# Editorial Principles

Every specification document follows the same editorial discipline.

1. Each section answers exactly one question.
2. Normative statements use RFC 2119 terminology (MUST, SHOULD, MAY, MUST NOT).
3. Informative material appears only in appendices.
4. Documents introduce no implementation technology.
5. Documents introduce no concepts owned by later specifications.
6. Later documents may extend earlier documents but SHALL NOT contradict them.

---

# Repository Layout

```text
docs/
├── SPECIFICATION.md
└── spec/
    ├── 000-vision.md
    ├── 010-ubiquitous-language.md
    ├── 020-domain-model.md
    ├── 030-invariants.md
    ├── 040-workflows.md
    └── 050-capabilities.md
```

---

# Normative Language

The key words **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and
**MAY** are to be interpreted as described by RFC 2119 and RFC 8174.

---

# Change Control

Changes to an Accepted document SHALL preserve the consistency of the
specification as a whole.

Normative changes require incrementing the document's major version.

Editorial and clarifying changes SHALL NOT alter the normative meaning of
previously accepted requirements.