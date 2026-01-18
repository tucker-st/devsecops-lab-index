# DevSecOps Lab Index

This repository serves as a single, authoritative index for my DevSecOps and container security lab repositories on my professional GitHub account.

The goal of this index is clarity, not completeness. Each repository demonstrates one capability with explicit scope and explicit non-goals.

Design principles:
- One capability per repository
- Evidence-first workflows
- Clear separation between visibility, assessment, and enforcement
- Artifacts over screenshots
- Composable, not monolithic

Account:
https://github.com/tucker-st

---

## Implemented Repositories

### Docker Image Hygiene
Status: Implemented

Purpose:
- Establish baseline visibility into local container image state
- Make changes observable through before-and-after comparison

What it demonstrates:
- Inventory capture before change
- Inventory capture after change
- Diffable artifacts showing what changed

Primary outputs:
- Before inventory
- After inventory
- Diff report
- Execution logs

Repository:
https://github.com/tucker-st/docker-image-hygiene

---

### Docker Image Assurance
Status: Implemented (v0.1.0)

Purpose:
- Produce reviewable evidence about container image contents and known vulnerabilities

What it demonstrates:
- SBOM generation
- Vulnerability assessment using known data sources
- Human-readable assurance summary

Primary outputs:
- out/sbom.json
- out/vuln.json
- out/summary.md

Repository:
https://github.com/tucker-st/docker-image-assurance

Release:
v0.1.0

---

### Policy Enforcement Foundations
Status: Implemented (v0.1.0)

Purpose:
- Demonstrate policy evaluation and enforcement gating using explicit rules

What it demonstrates:
- Policy-as-code evaluation
- Deterministic allow or deny decisions
- Explainable enforcement outcomes

Primary outputs:
- out/decision.json
- out/summary.md

Repository:
https://github.com/tucker-st/policy-enforcement-foundations

Release:
v0.1.0

---
## End-to-End Workflow

For a single, step-by-step guide demonstrating how the repositories in this index
work together, see:

CONTAINER_IMAGE_CONTROL_CHAIN_GUIDE.md

---

## How These Repositories Fit Together

The repositories are designed to form a simple, composable control chain.

1) Container Image Hygiene
- Establishes baseline visibility into local container image state
- Captures before-and-after inventories to make changes observable
- Produces diffable artifacts that support review and troubleshooting

Scope clarification:
- Container image hygiene focuses on awareness and traceability of change
- It does not assess risk, severity, or compliance
- It does not make allow or deny decisions

---

2) Container Image Assurance
- Produces reviewable evidence about container image contents and known vulnerabilities
- Generates machine-readable artifacts suitable for downstream processing
- Provides a human-readable summary to support review

Scope clarification:
- Container image assurance evaluates image contents against known data sources
- It does not enforce policy or make allow or deny decisions
- It does not modify images or environments

---

3) Container Image Policy Enforcement
- Evaluates evidence produced by upstream processes against explicit policy rules
- Produces a deterministic allow or deny decision
- Generates machine-readable and human-readable decision artifacts

Scope clarification:
- Container image policy enforcement consumes evidence; it does not generate it
- Policy decisions are explicit and explainable
- Enforcement logic is intentionally decoupled from hygiene and assurance tooling

---

## Control Chain Summary

Container Image Hygiene provides visibility into change.

Container Image Assurance provides evidence about image contents and known issues.

Container Image Policy Enforcement evaluates evidence and produces an explicit decision.

Each layer is intentionally independent. Evidence must exist before enforcement. Enforcement is explicit and explainable.

---

## Planned (Future)

Enforcement and Policy Expansion

Intent:
- Add optional examples that demonstrate enforcement patterns such as CI gating or admission-style checks

Non-goals:
- No enterprise policy framework
- No broad compliance claims
- No mixing enforcement logic into hygiene or assurance repositories

---

## Status

This index evolves as labs are added or refined.
Repositories are considered stable unless explicitly marked otherwise.
