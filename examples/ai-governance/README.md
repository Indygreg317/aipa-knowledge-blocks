# AI Governance Examples

This directory contains AIPA Knowledge Block examples focused on governed AI workflows, human oversight, policy-aware orchestration, tool-use control, high-risk action routing, and audit-ready AI system behavior.

AIPA public material is available at [aipa.network](https://aipa.network).

---

## Purpose

AI governance examples show how Knowledge Blocks can structure the rules, constraints, and review paths that surround AI-assisted systems.

These examples demonstrate how AI governance knowledge can be:

- represented as structured operational guidance
- tied to invocation conditions
- reviewed by human or organizational authority
- checked against policy and risk requirements
- revalidated before tool use or workflow action
- audited after model-assisted decisions

---

## Current Examples

| Example | Format | Purpose |
|---|---|---|
| [High-Risk AI Action Escalation](high-risk-action-escalation.md) | Narrative | Shows how a high-impact AI-assisted action is escalated for human review instead of executing automatically |
| [High-Risk AI Action Escalation JSON](high-risk-action-escalation.json) | JSON | Machine-readable Knowledge Block example for high-risk AI action escalation |

---

## Example Concepts

Future examples may include:

- model-assisted decision review
- external tool-use approval
- human oversight routing
- policy exception handling
- sensitive data handling rule
- AI-generated recommendation audit record
- agent action authorization check

---

## Suggested Controls

AI governance Knowledge Blocks often require:

- human review for high-impact actions
- strict authority validation
- prohibited action lists
- audit log required
- block on policy mismatch
- evidence freshness for policy references
- escalation when confidence, context, or authority is insufficient

---

## Implementation Boundary

These examples are reference artifacts only. Real AI governance deployment should be reviewed against the target system, applicable laws, organizational policy, user-impact risks, security requirements, and human oversight obligations.

A Knowledge Block can structure governance logic, but it does not replace accountability, oversight, or responsible deployment practice.
