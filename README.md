# DevSecOps Lab Index

This repository is a single, authoritative index for my DevSecOps and cloud security lab repositories on my professional GitHub.

Principles:
- Each repo demonstrates one capability clearly (no monoliths).
- Each repo has explicit scope and explicit non-goals.
- Outputs should be evidence-producing (artifacts, logs, decisions).
- Labs are composable: hygiene -> assurance -> enforcement.

Account: https://github.com/tucker-st

---

## Implemented Repositories

### 1) Docker Image Hygiene (Implemented)
Purpose:
- Maintain change visibility for local Docker images by capturing before/after state and producing a diff report.

What it demonstrates:
- Operational hygiene and change tracking for existing images
- Evidence artifacts suitable for review (before/after inventories, diffs, logs)

Repository:
- https://github.com/tucker-st/docker-image-hygiene

---

### 2) Docker Image Assurance (Implemented, tagged v0.1.0)
Purpose:
- Produce reviewable container image assurance artifacts using containerized tooling.

What it demonstrates:
- SBOM generation (machine-readable)
- Vulnerability assessment output (machine-readable)
- A human-readable summary for reviewers

Primary outputs:
- out/sbom.json
- out/vuln.json
- out/summary.md

Repository:
- https://github.com/tucker-st/docker-image-assurance

Release:
- v0.1.0

---

### 3) Policy Enforcement Foundations (Implemented, tagged v0.1.0)
Purpose:
- Demonstrate policy evaluation and enforcement gating using OPA, producing explicit allow/deny decisions and artifacts.

What it demonstrates:
- Policy-as-code evaluation
- Deterministic artifacts for review
- Gate semantics (exit 0 allow / non-zero deny)

Primary outputs:
- out/decision.json
- out/summary.md

Repository:
- https://github.com/tucker-st/policy-enforcement-foundations

Release:
- v0.1.0

---

## How These Repos Fit Together

A minimal, composable control chain:

1) Hygiene:
- Tracks what changed locally (before/after, diffs)
- Does not claim vulnerability assessment or enforcement

2) Assurance:
- Produces evidence (SBOM + vulnerability results)
- Does not enforce or block by itself

3) Enforcement:
- Consumes normalized evidence and makes an explicit decision (allow/deny)
- Produces reviewable decision artifacts

Design intent:
- Evidence should exist before enforcement.
- Enforcement should be deliberate and explainable.

---

## Planned (Future)

### Enforcement & Policy Expansion (Planned)
Intent:
- Add optional examples that demonstrate enforcement patterns (admission concepts, CI gating patterns) without becoming an enterprise policy engine.

Non-goals:
- No “one-click enterprise framework”
- No broad compliance claims
- No mixing enforcement logic into hygiene or assurance repos

---

## Status

This index evolves as labs are added or refined.
Repositories are considered stable unless explicitly marked otherwise.
