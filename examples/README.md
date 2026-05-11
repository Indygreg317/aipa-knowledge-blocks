# Examples

This directory contains practical examples and starter guides for **AIPA Knowledge Blocks**.

The examples show how structured knowledge can be represented, invoked, revalidated, allowed, blocked, escalated, and audited.

AIPA public material is available at [aipa.network](https://aipa.network).

---

## Purpose

Examples help connect the Knowledge Block framework to implementation practice.

They are intended to show:

- how a Knowledge Block can represent an operational decision
- how trigger and runtime conditions affect execution
- how approval differs from execution authorization
- how runtime revalidation can allow or block action
- how audit records preserve traceability
- how domain-specific starter areas can be expanded into practical playbooks

Examples are not production-ready policies. They are reference artifacts for learning, testing, and adaptation.

---

## Current Example Areas

| Example Area | Purpose | Status |
|---|---|---|
| [Execution Control](execution-control/) | Demonstrates allowed and blocked runtime execution decisions | Active examples |
| [AI Governance](ai-governance/) | Starter guide for governed AI workflows, human oversight, policy-aware orchestration, and tool-use control | Starter guide |
| [Compliance](compliance/) | Starter guide for compliance workflows, policy alignment, evidence review, and audit chains | Starter guide |
| [Operations](operations/) | Starter guide for operational decisions, deployment controls, incident response, and escalation | Starter guide |
| [Carbon and Sustainability](carbon/) | Starter guide for carbon reporting, sustainability workflows, methodology validation, and audit preparation | Starter guide |

---

## Current Execution-Control Examples

Narrative examples:

- [Allowed Execution Narrative](execution-control/allowed-execution.md)
- [Blocked Execution Narrative](execution-control/blocked-execution.md)

Machine-readable examples:

- [Allowed Execution JSON](execution-control/allowed-execution.json)
- [Blocked Execution JSON](execution-control/blocked-execution.json)

---

## Future Example Opportunities

Future additions may include:

| Example Set | Possible Focus |
|---|---|
| Compliance | Evidence sufficiency checks, policy exceptions, regulatory review workflows |
| Operations | Maintenance windows, rollback decisions, incident escalation, capacity thresholds |
| Carbon and Sustainability | Emissions methodology checks, supplier data review, sustainability claim validation |
| AI Governance | Human review routing, high-risk action escalation, tool-use authorization |
| Security | Access approval, privileged actions, containment workflows, incident classification |

---

## How to Read the Examples

Each example should clarify:

1. What decision or action is represented
2. What was true at approval or decision time
3. What changed at runtime
4. What revalidation checks were performed
5. Whether execution was allowed, blocked, deferred, degraded, escalated, or aborted
6. What audit record should remain

---

## Relationship to Templates

Templates help authors create new Knowledge Blocks.

Examples show how a Knowledge Block behaves in a scenario.

Use [`../templates/`](../templates/) when creating a new block. Use this directory when studying how blocks may be applied, tested, or explained.

---

## Implementation Boundary

These examples are simplified reference artifacts.

Before using a Knowledge Block in a real environment, teams should confirm:

- schema validity
- domain expert review
- policy alignment
- evidence freshness
- trust level
- verification status
- runtime controls
- authority requirements
- audit requirements
- applicable legal, compliance, safety, or security review

---

## Core Rule

A Knowledge Block should not execute merely because it exists or was previously approved.

It should execute only when current trust, verification, authority, evidence, risk, context, and policy conditions permit execution.
